# ground-init

Set up a local Linux or macOS desktop automatically using a Python script. Requires `PyYAML` (`pip install pyyaml`).

## But Why?

![](why.gif)

I got tired of setting up new GNOME desktops manually every time I created an `LXC` sandbox, and the day my Fedora desktop rebooted into emergency mode I realized it was time to automate the reinstall process. I later added macOS support via Homebrew.

The name is a pun on [`cloud-init`](https://cloud-init.io/) (which I use for everything), and the `YAML` format is meant to be as close as possible.

## Usage

```bash
python3 ground-init.py <config_file.yaml> [--steps <step1> <step2> ...]
```

You can execute specific steps (top-level keys in the `YAML` file like `packages`, `runcmd`, etc.) independently by listing them after `--steps`, or the script will execute all steps found in the file in the order they appear. Python 3.7+ maintains dictionary insertion order, so the ordering in the file is respected.

## Sample Files

The [`samples`](samples) directory contains various examples for different operating systems and tasks, including:

* Setting up Fedora (`fedora-40.yaml`, `fedora-daw.yaml`) and Debian/Ubuntu (`ubuntu-xfce-rdp.yaml`, `syncthing.yaml`) systems.
* Configuring specific services like Proxmox (`proxmox.yaml`), Piku PaaS (`piku.yaml`), Network UPS Tools (`network-ups.yaml`), or Bluetooth PAN (`btpan.yaml`).
* Building software from source (`onnxstream.yaml`).
* Setting up hardware like USB Ethernet gadgets (`ethernet_gadget.yaml`, `radxa_zero_ethernet_gadget.yaml`) or Wi-Fi adapters (`rtl8188eus.yaml`).

These can be adapted for different needs and operating systems (including macOS, using `brew` and `cask:` prefixes in the `packages` section).
