---
layout: post
title: Perfect workspace
tags: linux
---

As you know there are so many distros, and this is not a good point at all.
At this post I will try to explain the perfect workspace I get after try lots of combinations.

## Table of contents
    - [What is the perfect workspace any way ?](#what-is-the-perfect-workspace-any-way)
    - [Current approach](#current-approach)
    - [Important apps](#important-apps)

---

## [What is the perfect workspace any way ?](#what-is-the-perfect-workspace-any-way)
I compare every try with the current state of Mac:
    - stability
    - simplicity
    - efficiency
    - base apps availability
    - elegancy and modern

## [Current approach](#current-approach)
- I will use fedora workspace (Gnome Edition)
- I use the previous version before the current one (for example I use fedora 37 while the current one is fedora 38)
    - why? this will increase stability a lot
- fedora life cycle is 13 months (upgrade only every these 13 months)
- enable secureboot
- you must encrypt everything except `/boot` and `/boot/efi` partitions
- partitions map:

    | # | name | path | filesystem | size |
    |:-:|:----:|:----:|:----------:|:----:|
    | 1 | EFI  | /boot/efi | fat32 | 512 MB |
    | 2 | boot | /boot | ext4 | 1024 MB |
    | 3 | fedora | ... | luks2/BTRFS | rest |
    |   | @ | / | | |
    |   | @home | /home | | |
    |   | @var | /var | | |
- This is the default scheme except for /var
- enable autologin
- install flatpak only apps


## [Important apps](#important-apps)
- `firewalld-config`: this is the firewall GUI, you will need it to create a configuration per connected network
- `timeshift`: This is your backup app that use BTRFS snapshot
    - this will create a snapshot for `/` and `/home` everyday, keeping only 5 snapshots
    - you can revert at anytime (you need to reboot after reverting)
    - if the system refused to open at all:
        - get any distro
        - install timeshift on it
        - choose the disk that contains the snapshots
        - revert back to a working snapshot
        - reboot