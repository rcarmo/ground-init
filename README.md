# ground-init

Set up a local Linux desktop automatically using a (zero-dependencies) Python script.

## But Why?

![](why.gif)

I got tired of setting up new GNOME desktops manually every time I created an `LXC` sandbox, and the day my Fedora desktop rebooted into emergency mode I realized it was time to automate the reinstall process.

The name is a pun on [`cloud-init`](https://cloud-init.io/) (which I use for everything), and the `YAML` format is meant to be as close as possible.

## Usage

```bash
python3 ground-init.py [target [target]]
```

You can execute each target in the `YAML` file independently if you want, or the script will blindly go through them all. Sane ordering isn't implemented (yet) because Python 3.10 and later have ordered dictionaries, so the ordering in the file works for me (but I intend to enforce some restrictions).

## Sample Files

The current samples include the baseline install I do on a blank Fedora 37 machine, the deployment of my [Piku PaaS](https://github.com/piku) (which is almost exactly the same file I use for `cloud-init` bootstrapping of VM instances) and configuration of Bluetooth PAN on Debian. Editing these for other Linux distributions (or for macOS) should be trivial and is left as an exercise to the reader.
