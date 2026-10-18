---
id: inbox_ab7867db
source: ecc-releases
source_type: rss
url: "https://github.com/affaan-m/ECC/releases/tag/v2.2.3"
author: "affaan-m"
published_at: 2026-10-01T23:59:38+00:00
fetched_at: 2026-10-18T02:56:53.715489+00:00
content_hash: "c234e7909a8bb04503acc6c10104e988e1b0a4dda245aca209d9dc90cfd76f51"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.2.3

ECC 2.2.3 
 ECC 2.2.3 is a naming and release-reliability update. The project is called ECC 
everywhere it ships, starting with the pi/core profile, and the release 
workflow now waits long enough for npm to serve a freshly published version. 
 Naming 
 
 pi/core no longer expands the project name: its README and the bundled 
 blueprint skill refer to ECC only. The profile contents are otherwise 
unchanged: 123 curated skills and 24 prompt commands, 35,006 characters of 
skill description text. 
 Downstream packagers need no changes. The package is still ecc-pi-core , the 
directory is still pi/core/ , and existing install paths keep working. 
 
 Release workflow 
 
 After npm publish , the release workflow polls the registry for up to five 
minutes before verifying the published artifact. In 2.2.2 it gave up after 
about 30 seconds while npm was still processing the upload, so the run failed 
before promoting latest and creating the GitHub Release, and had to be 
re-run. 
 
 Downstream consumption is unchanged: poll /releases , download 
 archive/refs/tags/vX.Y.Z.tar.gz , pin its sha256, copy pi/core/ , and load it 
offline.