# doc-inception

Docs on how to build a private/secure life from the ground up with automation
and configs to follow. All commits will be signed, let me know if you'd like
to contribute.

This is paranoid for a reason. There is no threat model as we are considering
the worst case scenario in all directions.

## Preferred inception situation

Inspect your hardware, remove/jumper with resistors where possible for 
hardware that is insecure/unneccessary or not trusted. Looking up the 
integrated controllers on your PC motherboard may surprise you - such as
iPhone audio ICs in specific Thinkpads.

In a perfect world, you can do this offline, have trusted releases, and have
a machine you can wipe all firmware, software, etc. from. In reality, if 
under pressure from a government entity or other threats to safety/life - 
this is not possible.

**The goal is to minimize compromise until in a secure state. Do your best,
learn along the way. Not having a secure environment and moving towards one
will teach you way more than you thought possible.**

## Preferred firmware

Something open-source such as Coreboot and its derivatives. You can compile
your own for unsupported configurations with the right know-how and tools.
It may involve connecting hardware to chips on your motherboard.

## Table of contents

- [OS](./os/OS.md)
- [Development environment](./dev/Development%20Environment.md)
    - [Compilers](./dev/Compilers.md)
- [Applications](./apps/Applications.md)

