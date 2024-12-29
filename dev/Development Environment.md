# Development Environment

As I'm putting myself through Microsoft hell at the moment to hopefully reach
the widest audience possible, my development environment is MSYS2/mingw using 
UCRT64 as its configuration. For those unaware, UCRT is the universal C runtime
that appeared in Windows 10. It has better compatibility with MSVC and is
included with the OS. This is the desirable route to avoid installing tons
of tools through the Visual Studio installer and use open-source tooling.

Alright, let's begin.

## Install a release, then build it from source

Yes, you heard that correctly. We are going to download a release of MSYS2
and use its tooling to build its installer and reinstall it. This may seem
redundant and unneccessary, but anyone who has chased down security/privacy
tools in various repos has probably seen things like a "trojan-source" CI
job in Gitlab or commits on non-release branches adding "extra" features.

Grab a release from [here](https://github.com/msys2/msys2-installer/releases)
and install it.

Once installed, let's configure git.

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


