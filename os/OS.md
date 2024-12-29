# OS

Your operating system matters more than you'd imagine. If you want to get shit
done without worrying about added features and hoops to jump through on windows
use one of my recommended distros below. However, this guide is being completed
in Windows to help a very widely deployed OS's members who need security and
privacy.

## Linux/BSD distros

- Gentoo (my personal preference)
- Arch Linux (my runner up if you don't mind using binaries over source)
- FreeBSD
- DragonflyBSD

## Windows

If you are going to run Windows, they don't give a shit about consumers with
little money - so we are going to use a few workarounds to bypass this. This
guide requires at least a Pro edition of Windows 10 or 11, with preference
being Windows Enterprise IoT as it is stripped down and we can remove Edge
with a trick. I will show you how to convert whatever edition of Windows 
you are running to a desired edition.

Download official Microsoft Windows ISO images, PDFs that contain their hashes,
and verify them after the download completes. You can use the following
powershell script to verify Enterprise IoT.

```powershell
(Get-FileHash '.\26100.1.240331-1435.ge_release_CLIENT_IOT_LTSC_EVAL_x64FRE_en-us.iso').Hash -eq 8ABF91C9CD408368DC73AAB3425D5E3C02DAE74900742072EB5C750FC637C195
```

In order to remove Edge and Edge WebView we can change the region to the
European Union - more on this later.

For older hardware, there may be a need to bypass TPM checks - in that case
search the URL in references. It has an article describing how to do this.
The IoT image bypasses a lot of these checks if you are starting from scratch.

If you are on a version of Windows 10/11 that won't convert to a Pro edition
or higher, clear everything possible with the `slmgr` command and make the
registry entries described in the article below to modify what the installer
sees. You can find base keys for each edition on Microsoft's website.

## References

- https://web.archive.org/web/20241122134815/https://habr.com/ru/articles/828670/
-
