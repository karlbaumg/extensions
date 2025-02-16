# binder-linux

This extension provides the kernel module needed for Android-style IPC mechanisms through the binder driver.

## Installation

See [Installing Extensions](https://github.com/siderolabs/extensions#installing-extensions).

## Usage

Enable the module in Talos machine config with the required configuration:

```yaml
machine:
  kernel:
    modules:
      - name: binder_linux
        parameters:
          - devices=binder,hwbinder,vndbinder
```

## Verifying

You can verify the module is enabled by reading `/proc/modules` where it should show the module is live:

```bash
❯ talosctl -n <node-ip> read /proc/modules
binder_linux 151552 - - Live 0xffffffffc0414000
```

You can also verify the binder devices are present in `/dev`:

```bash
❯ talosctl -n <node-ip> ls /dev | grep binder
binder
hwbinder
vndbinder
``` 