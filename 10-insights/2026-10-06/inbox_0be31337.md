---
id: inbox_0be31337
date: 2026-10-06
source_ref: "[[00-inbox/2026-10-06/0102-lobsters-ai-burn-0-22-0-faster-builds-easier-extensi-a9be]]"
title: "Burn 0.22.0: Faster Builds, Easier Extensions, and Smarter Autotuning"
url: https://tracel.ai/blog/release-0.22.0/
source: lobsters-ai
published_at: 2026-10-06T18:57:25-05:00
fetched_at: 2026-10-25T01:26:32.360287+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Burn 模型不再綁定後端型別，改由 device 決定執行位置，從而加快重新編譯與執行。 **Why** 原本模型型別一路帶著 B: Backend，應用程式編譯時必須拉進整條依賴鏈，每次改動都要長時間重編。 **How** 以 Tensor → Bridge → Dispatch → Backend 分層做型別抹除，並加入自適應記憶體池、自動調校與 CUDA/HIP graph replay。 **What** 官方測試中，CNN 的 median rebuild 從 28.42 秒降到 4.57 秒、transformer 從 14.73 秒降到 1.00 秒；CNN 訓練吞吐量因卷積優化提升 80%；並新增 LoRA/QLoRA 與 ONNX export。"
key_points:
  - "移除使用者 API 的 backend 泛型，改由 device 選擇執行後端；官方測試中 rebuild 最多快 15 倍"
  - "自適應記憶體池使 CNN 峰值 VRAM 由 956 MiB 降到 486 MiB，transformer 由 3,486 MiB 降到 2,868 MiB"
  - "新增 LoRA/QLoRA 與 ONNX export，CubeCL Environment 可匯出並隨應用程式發布編譯與調校快取"
tags: [deep-learning-framework, burn, cubecl, lora, compile-time]
topics: [engineering.architecture, engineering.inference]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Burn 0.22.0: Faster Builds, Easier Extensions, and Smarter Autotuning

讓 Burn 模型不再綁定後端型別，改由 device 決定執行位置，從而加快重新編譯與執行。 **Why** 原本模型型別一路帶著 B: Backend，應用程式編譯時必須拉進整條依賴鏈，每次改動都要長時間重編。 **How** 以 Tensor → Bridge → Dispatch → Backend 分層做型別抹除，並加入自適應記憶體池、自動調校與 CUDA/HIP graph replay。 **What** 官方測試中，CNN 的 median rebuild 從 28.42 秒降到 4.57 秒、transformer 從 14.73 秒降到 1.00 秒；CNN 訓練吞吐量因卷積優化提升 80%；並新增 LoRA/QLoRA 與 ONNX export。

### 重點
- 移除使用者 API 的 backend 泛型，改由 device 選擇執行後端；官方測試中 rebuild 最多快 15 倍
- 自適應記憶體池使 CNN 峰值 VRAM 由 956 MiB 降到 486 MiB，transformer 由 3,486 MiB 降到 2,868 MiB
- 新增 LoRA/QLoRA 與 ONNX export，CubeCL Environment 可匯出並隨應用程式發布編譯與調校快取

**原文：** [lobsters-ai](https://tracel.ai/blog/release-0.22.0/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Simpler Models, Faster Builds

Easier Custom Operations

Faster Execution, Better Memory Management

Smarter Autotuning and Runtime Execution

New Compiler and Kernel Foundations

Fine-Tuning with LoRA and QLoRA

Remote Compute

Export Burn Models to ONNX

Upgrading to Burn 0.22

What's Next

Memory That Adapts to the Workload

CubeCL Environment and Deployment Caches

Controlling What Gets Trained

Quantized Base Weights

Burn 0.22 makes it easier to build applications, integrate custom kernels, and put models to work. In the previous release, we introduced burn-dispatch and started working toward removing backend generics from the user API with two goals in mind: simplify application code and improve compilation times. With this release, your code no longer carries backend type parameters, execution is instead selected through the device. In our tests, these changes made rebuilds up to 15× faster.

Beyond the API changes, we've improved execution across CPUs and GPUs with adaptive memory management, smarter autotuning, graph replay, and changes to the compiler and kernel foundations. The new CubeCL Environment lets applications reuse warmed compilation and autotuning caches on compatible targets. This release also adds support for adapting existing models with LoRA and QLoRA, ONNX export, and expanded support for remote compute. This post covers the major changes. The full list of improvements and fixes is available in the release notes .

Until now, choosing a backend affected the types throughout a Burn application. A model carried a B: Backend type, from its layers all the way down to their respective parameters, and tensor functions had to propagate it. This gave us a flexible architecture, but it also tied application code to a large dependency chain during compilation.

In 0.22, that backend parameter disappears from the user-facing API. The change is visible even in a small model:

The device now selects how and where execution happens. Enable the corresponding Cargo features, then choose a device when initializing the model and its inputs:

Training follows the same pattern, which means the B: AutodiffBackend no longer exists in application code. Instead, autodiff context is configured on the device and inherited by the tensors.

Underneath, operations follow Tensor → Bridge → Dispatch → Backend . The bridge hides the concrete backend representation from the high-level tensor API, breaking the dependency chain that previously reached into application code. This type erasure reduces recompilation when you make changes to your project. The dispatch, on the other hand, routes each operation to the corresponding backend, allowing a single application to easily enable mutiple backends. The Backend trait remains at the core of Burn to support backend implementations and custom operations.

To give you an example of how this affects compilation times, we tested model changes in two separate projects. One uses a small CNN with Burn's built-in learner, the other uses a transformer with a custom training loop. Adding or removing a hidden layer in the CNN benchmark reduced the median release rebuild from 28.42 seconds to 4.57 seconds. For the transformer, alternating equivalent feedforward expressions reduced its rebuild from 14.73 seconds to 1.00 second. With these two setups, we can see how compilation improves across different models and dependency footprints.

MNIST enables Burn's train feature and uses its learner. The transformer uses a custom training loop. Model edits: add or remove a hidden linear layer with GELU and dropout for MNIST, and alternate equivalent feedforward expressions for the transformer. Bars and labels show medians across three runs. Error bars show the observed min-max range. Each metric has its own linear scale starting at zero.

Custom operations are still implemented using backend primitives, even though the application code no longer carries backend generics. If you already had a backend extension trait, its definition and implementations remain pretty much the same. The #[backend_extension] macro connects it to the dispatch system, so you can expose your operation through a tensor function without backend generics. Here is an excerpt from our custom CubeCL kernel example , which combines matrix multiplication, bias addition, and ReLU:

The output_shape helper describes the output before the kernel runs. With that metadata, the macro generates registration for lazy execution through Fusion, alongside dispatch routing. The full example includes the kernel and its backward implementation, so callers can use the same function for training and inference.

This gives extension authors control over the implementation, including a custom backward pass. By default, custom operations act as boundaries in the fusion graph. Operations on either side can still be fused, but combining them with the custom operation requires a dedicated fusion optimization. The extension guide explains the complete workflow. Burn's linear algebra and signal processing functionality now use this approach through the burn-linalg and burn-signal extension crates.

While building the new AI engine on top of Burn (more on that in What's Next ), we developed a way to tune memory pools using allocation statistics collected during a dry run. That work became the basis for CubeCL's new memory management. We also improved performance across CubeCL and CubeK, including several convolution optimizations.

To measure the impact, we compared Burn 0.21 and 0.22 on two training workloads, using the same two projects , running in FP32 with CUDA on an NVIDIA GeForce RTX 4050 Laptop GPU. Each workload ran three times per version, with 50 warmup steps followed by 500 measured steps. The graphs show medians across those runs, with error bars for the observed min-max ranges.

FP32 on an NVIDIA GeForce RTX 4050 Laptop GPU, with 50 warmup and 500 measured steps per run. Step time is the mean within each run. Bars and labels show medians across three runs. Error bars show the observed min-max range. Each metric has its own linear scale starting at zero.

The convolution optimizations helped increase training throughput by 80% in our CNN benchmark. This work includes faster convolution gradient computation, an improved direct kernel for transposed convolution, and a dedicated BatchNorm training operation with an optimized backward pass.

We also improved how fusion handles tensor layouts to avoid unnecessary copies and allow more operations to be fused after an unfusable operation.

CubeCL already reused device memory through pools, avoiding repeated allocations. But when the pool sizes don't match the workload, they can reserve more memory than the tensors need. The new adaptive memory pools adjust their allocation sizes around the workload, without requiring users to configure pool sizes for each model.

As larger allocations arrive, the pools adjust their page sizes and release outdated pages once they become empty. The runtime can also move live allocations to free them sooner, while keeping frequently changing small allocations in a separate pool. Memory reports now show both used and reserved memory, so you can see how much of the reserved space your workload actually needs. This is available through Burn's Device API, which exposes more CubeCL utilities in this release.

After warmup, median and peak VRAM usage were identical in each run. Temporary startup bandwidth-probe allocations are excluded. Bars and labels show medians across three runs. Error bars show the observed min-max range. Each metric has its own linear scale starting at zero.

As the benchmarks show, peak VRAM usage after warmup fell from 956 to 486 MiB for the CNN, which is nearly half. For the transformer, median peak VRAM fell from 3,486 to 2,868 MiB, a 17.7% reduction. These measurements represent process VRAM after warmup. They exclude CubeCL's temporary startup allocations used to measure the device's memory bandwidth and guide autotuning.

For convolutional models, improvements cover both training and inference. Convolution gradients have more efficient execution paths, transposed convolution has a dedicated direct kernel, and BatchNorm training uses a dedicated operation with a closed-form backward pass.

In the previous release post, we discussed using hardware throughput to decide when to stop autotuning. The adaptive autotuning scheduler uses measured compute and memory throughput to estimate a performance target for an operation. When a candidate reaches the expected performance ,the tuner can stop exploring. It also eliminates weaker candidates early and adjusts how much measurement each candidate needs.

We also reduced overhead for repeated execution by adding graph capture and replay support on CUDA and HIP. This lets CubeCL reuse a sequence of kernel launches without repeating much of the launch preparation. For WGPU, replay is supported via a software graph that retains resolved pipelines and bindings.

CubeCL already cached compiled kernels and autotuning results between runs, but we've reworked that caching around the new CubeCL Environment , which groups those together in a named environment. You can populate an environment's caches ahead of time, export them together, and ship them with your application. The environment also provides a common API for runtime configuration and cache storage across native applications, WebAssembly, and no_std .

We also expanded profiling support across Burn and CubeCL, including device timing on CUDA and HIP to help identify where execution time is spent.

The work on custom operations and portable execution also required changes deeper in the stack. CubeCL has migrated its compiler infrastructure to Pliron , giving us a common foundation for representing, transforming, and lowering kernels. Its LLVM compiler now includes targets for AMD and NVIDIA GPUs, extending the LLVM path beyond CPU execution.

CubeK's tile abstraction addresses another challenge: complex kernels often need the same pieces of logic for loading data, staging it in memory, computing on it, and writing results. Making those pieces reusable lets kernel authors compose implementations for different layouts, precisions, and hardware capabilities.

That work is already used in tiled matrix multiplication, attention, and interpolation implementations. It also gives us a better foundation for extending and optimizing those kernels. Together with the backend extension API, it connects application-level customization to reusable compute building blocks further down the stack.

Burn 0.22 adds support for adapting existing models to new tasks with LoRA and QLoRA. LoRA keeps the base weights frozen and trains low-rank adapters, reducing the number of parameters that need gradients and optimizer state. QLoRA also keeps the base weights quantized to reduce their storage requirements.

You can attach adapters to an existing model without changing its layers or forward pass. Initialize the model on an autodiff device, select the parameters to adapt, and apply LoRA:

This freezes the base floating-point parameters and attaches trainable adapters to matching two-dimensional weights. LoRA is built on a generalized weight reparameterization mechanism: a parameter keeps its stored base and an attached module computes its effective value. Adapter parameters participate in autodiff, optimization, device transfers, and checkpointing through the existing module infrastructure.

Parameter groups also connect fine-tuning to the optimizer. You can keep the base weights frozen, enable a task-specific head, and assign different optimizers or learning-rate policies to the head and adapters. For example, after attaching adapters to a model with a classifier head:

The classifier uses the default optimizer, while the adapters use their own configuration. Learning-rate schedulers support the same grouping model, so optimizer choice

[... truncated for safety ...]

</details>