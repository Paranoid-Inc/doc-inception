# Wireguard

Wireguard is a VPN client that is at a lower layer than most. It has a small 
codebase and is reasonably secure. Always get Wireguard configs from your
VPN provider and abstain from using their VPN client. We will set up
killswitches ourselves and most of the other things these provide.

## Pre-requisites

* MSYS2 environment
* Golang
* Make
* Required library dependencies and imagemagick

The provided patch removes unused architectures, uses the system golang and
removes switches from `go build` that are provided in 1.18.

Patch can be viewed [here](./wireguard-makefile.patch)

```bash
$ git clone git@github.com:WireGuard/wireguard-windows.git
$ git tag -l # find the latest release
$ git checkout <latest release here>
$ git apply wireguard-makefile.patch
```
