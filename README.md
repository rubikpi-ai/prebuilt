# RUBIK Pi 3 CHICDK 1.0.52

`chicdk-kodiak_1.0.52_armv8-2a.tar.xz` provides the ARM64 CHI runtime with IMX219 and IMX477
support on either RUBIK Pi 3 CSI connector. It includes four module binaries,
both tuning binaries, eight single/dual camera profiles, the updated sensor map,
and the reference camera profiles. The CHI override, features, nodes and sensor
drivers were cross-compiled together. The SDK's unchanged SHDR prebuilt is retained.

Use the complete archive as the CHI payload of `camxlib-kodiak_1.0.52`.
The image supplies the matching CamX core, algorithms, camera driver and firmware.
This is not a drop-in runtime for CamX 1.0.35 / QLI 2.1.1 or Ubuntu.
The supplied SHDR binary requires glibc 2.43; the runtime also requires
GLIBCXX 3.4.32 and an OpenCL loader when SHDR is enabled.

```sh
sha256sum -c SHA256SUMS
tar -xf chicdk-kodiak_1.0.52_armv8-2a.tar.xz
sha256sum -c FILES.sha256
```

In Yocto, replace the official `chicdk-kodiak_1.0.52_armv8-2a.tar.gz`
entry in `camxlib-kodiak_1.0.52`'s `SRC_URI` with this archive and set its
named download checksum to `c3584696228ec7629c4bd7c32c396b167ecedbb77bf37975a39c8148fe8cf5a2`. Keep the other CamX archives unchanged.
Install all of `usr/lib/`; selecting only the added sensor files omits the
new logical camera profiles and sensor map. Retain the documents under
`usr/share/doc/chicdk-kodiak/`.

Cross compilation, all 60 AArch64 ELF libraries, runtime symbol dependencies,
SONAMEs, library links, configuration selection and archive checksums were checked.
Camera operation with this package has not yet been tested on a board.
Tuning data is regenerated with the new schema; it is not a new IQ calibration.
`BUILD-INFO.json` records the build baseline and verification limits;
`MANIFEST.json` records file hashes and library link targets.

Vendor terms and notices are retained under `usr/share/doc/chicdk-kodiak/`.
This package grants no additional rights.
