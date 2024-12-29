# MSYS2

Grab a release from [here](https://github.com/msys2/msys2-installer/releases)
and install it.

Once installed, launch the UCRT64 environment and configure git.

```bash
$ pacman -S git vim openssh
$ mkdir -p ~/.ssh && chmod 700 ~/.ssh
$ touch ~/.ssh/config && chmod 600 ~/.ssh/config
$ ssh-keygen -o -a 100 -t ed25519 # Follow prompts to generate your key and set a password
$ vim ~/.ssh/config
```

Add the following to avoid firewall issues/configuration when using git
over SSH.

```
Host github.com
        HostName ssh.github.com
        User git
        Port 443
        IdentitiesOnly yes
        IdentityFile ~/.ssh/id_ed25519 # or whatever you output the file as
        Compression yes
```

```bash
$ # Create some directory for source code, a dev drive segregates code on Win
$ git clone git@github.com:msys2/msys2-installer.git
$ cd msys2-installer
$ ./make-msys2-installer # if you need dependencies research and install them
```

When your MSYS2 installer is built, remove the old MSYS2 installation and
reinstall yours. You should probably sign your releases and commit changes
to packages, generate hashes, etc. but this is simply a guide for getting you
to a secure state.

Reinstall the previous packages and configuration if removed.
