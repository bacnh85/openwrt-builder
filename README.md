# OpenWrt-Builder

OpenWrt builder for OpenWrt based - based on [wlan-ap](https://github.com/Telecominfraproject/wlan-ap) and [gl-infra-builder](https://github.com/gl-inet/gl-infra-builder).

Note: this is based on OpenWrt 23.05.

## Building

### Doing a native build on Linux

Follow the manual steps below:

1. Clone and set up the tree. This will create an `openwrt/` directory.
```shell
./setup.py --setup    # for subsequent builds, use --rebase instead
```

2. Select the profile and base package selection. This setup will install the
   feeds and packages and generate the `.config` file.
```shell
cd openwrt
./scripts/gen_config.py buffalo_wzr-hp-g302h-a1a0
```

3. Build the tree (replace `-j 8` with the number of cores to use).
```shell
make -j 8 V=s
```

### Build output

The build results are located in the `openwrt/bin/` directory:

| Type             | Path                                                 |
| ---------------- | ---------------------------------------------------- |
| Firmware images  | `openwrt/bin/targets/<target>/<subtarget>/`          |
| Kernel modules   | `openwrt/bin/targets/<target>/<subtarget>/packages/` |
| Package binaries | `openwrt/bin/packages/<platform>/<feed>/`            |

### Repository structure

Build files:
- `setup.py` - Clone and set up the tree
- `config.yml` - Specifies OpenWrt version and patches to apply

### Repository structure

Directories:
- `feeds/` - OpenWiFi feeds
- `patches/` - OpenWiFi patches applied during builds
- `profiles/` - Per-target kernel configs, packages, and feeds

## Credits

This project is based on [wlan-ap](https://github.com/Telecominfraproject/wlan-ap) and [gl-infra-builder](https://github.com/gl-inet/gl-infra-builder).