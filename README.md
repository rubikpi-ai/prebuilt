# RUBIK Pi 3 CHICDK binaries for QLI 2.1.1

The `chicdk-qli2.1.1` branch provides the complete ARM64 CHICDK runtime for the
RUBIK Pi 3 integration with QLI 2.1.1 and CamX 1.0.35.

## Contents

`chicdk-kodiak-rubikpi3_1.0.35-qli2.1.1_armv8-2a.tar.xz` contains 94 runtime files and 56 library links under
`usr/lib/`, including the CHI override, feature and node libraries,
IMX219 and IMX477 sensor libraries, four CAM1/CAM2 module configurations and
both tuning binaries. It also retains the SDK's reference runtime assets.
Most files are under `usr/lib/camx/kodiak/`; the versioned
`libcamxchiofflinepostproclib_kodiak.so.1` library is directly under `usr/lib/`.

The image must provide matching CamX core, algorithms, camera driver and
firmware separately. `nativehaltest` remains part of the CamX test package.
This archive contains no SDK tools, source code, headers or tuning XML.

## Verify and integrate

```sh
sha256sum -c SHA256SUMS
tar -xf chicdk-kodiak-rubikpi3_1.0.35-qli2.1.1_armv8-2a.tar.xz
sha256sum -c FILES.sha256
```

`MANIFEST.json` records runtime, documentation and build-info file hashes,
modes and link targets.
`BUILD-INFO.json` records the target release, compiler and ABI baselines,
and binary integrity metadata.

For a Yocto recipe, use a fixed commit download URL and the archive SHA256
from `SHA256SUMS`. Install the entire `usr/lib/` tree and retain the documents
under `usr/share/doc/chicdk-kodiak/`. Keep this runtime paired with the
QLI 2.1.1 CamX 1.0.35 packages; Ubuntu or newer SDK compatibility has not
been established.

## Terms

These are vendor binary assets. The full SDK terms and notices are retained
as `LICENSE.QCOM-2.txt` and `NOTICE`, alongside original sensor and tuning
notices under `usr/share/doc/chicdk-kodiak/`. This repository grants no
additional rights; redistribution is subject to the applicable vendor terms.
