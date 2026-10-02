# MIRO A1 mobile OS upstreams

Purpose: preserve the candidate operating-system and hardware-enablement upstreams for the MIRO A1 so the choice does not need to be re-litigated later. This is an archive/reference list, not a decision to use one stack.

## Already in dilapidated-shed

- Linux kernel: https://github.com/dilapidated-shed/linux
  - Relevant upstream SC9863A / sp9863a-1h10 device-tree support belongs here.
  - The actual MIRO A1 DTB/DTBO still needs to be extracted from the phone.

## GitHub projects to fork into dilapidated-shed

### LineageOS
- Manifest/root project: https://github.com/LineageOS/android
- This is a repo-manifest project; the full OS is many repositories.

### TrebleDroid / PHH GSI
Preserve the whole small core set:
- https://github.com/TrebleDroid/treble_manifest
- https://github.com/TrebleDroid/treble_experimentations
- https://github.com/TrebleDroid/device_phh_treble
- https://github.com/TrebleDroid/vendor_hardware_overlay
- https://github.com/TrebleDroid/treble_app

### Halium
Halium is the reusable Android-hardware bridge needed by Ubuntu Touch/Droidian-style ports.
- Organization: https://github.com/Halium
- Manifest/root: https://github.com/Halium/android
- Generic arm64 device: https://github.com/Halium/android_device_halium_halium_arm64
- Generic device: https://github.com/Halium/android_device_halium_halium
- Vendor config: https://github.com/Halium/android_vendor_halium_config

### Droidian
Preserve at least:
- https://github.com/droidian/droidian
- https://github.com/droidian/porting-guide
- https://github.com/droidian/halium-wrappers
- https://github.com/droidian/droidian-camera
- https://github.com/droidian-releng/rootfs-templates
- https://github.com/droidian-releng/android-image-flashing-template
- https://github.com/droidian-devices/devices.droidian.org

### Ubuntu Touch / UBports
This is a multi-repository project. Preserve the porting/build roots rather than pretending one repository is the OS:
- https://github.com/ubports
- https://github.com/ubports/halium_bootable_recovery
- https://github.com/ubports/ubports-pdk
- https://github.com/ubports/installer-configs
- https://github.com/ubports/ubports-installer
- Historical/porting documentation: https://github.com/ubports/docs.ubports.com

### Sailfish OS
Sailfish is also multi-repository, with some proprietary components. Preserve the open hardware/userland pieces that become relevant to the A1:
- Organization: https://github.com/sailfishos
- libhybris-related adaptation work should also be tracked from the mer-hybris/Sailfish ecosystem.
- Do not represent a Sailfish fork as a complete open-source Sailfish distribution; it is not.

## Non-GitHub upstreams to mirror/import into dilapidated-shed

### AOSP
Official source is on Android Git:
- https://android.googlesource.com/platform/manifest/
- https://android.googlesource.com/mirror/manifest/

The second manifest exists specifically to enumerate/mirror the projects hosted on the AOSP server. A GitHub copy in dilapidated-shed would be a mirror/import, not an upstream GitHub fork.

### postmarketOS
Official source is on postmarketOS GitLab:
- pmaports: https://gitlab.postmarketos.org/postmarketOS/pmaports
- pmbootstrap: https://gitlab.postmarketos.org/postmarketOS/pmbootstrap

pmaports is the device/package knowledge base; pmbootstrap is the build/flash tool. Preserve both.

### Mobian
Mobian moved its maintained source to Debian Salsa under the Mobian-team group:
- https://salsa.debian.org/Mobian-team
- image recipes: https://salsa.debian.org/Mobian-team/mobian-recipes

A copy in dilapidated-shed would be a mirror/import rather than a GitHub fork.

## MIRO A1 rule

Keep MIRO-specific hardware enablement separate from the choice of userspace. Reuse one hardware record/device tree/kernel effort across AOSP/Lineage/Treble, Halium-derived systems, postmarketOS, Mobian, and plain Debian/Alpine experiments wherever technically possible.

Do not delete candidates merely because another path looks easier today. dilapidated-shed is specifically the place to retain these experiments and upstream references.
