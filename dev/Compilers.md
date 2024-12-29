# Compilers

To ensure system security at very low levels, we need to think very hard
about protections and exploits that occur from memory corruptions and low
level operations/storage mechanisms such as your CPU's stack, heap, etc.
We need to mitigate things like Spectre. We will begin with GCC, I will
add Clang, TinyC, and Microsoft specific compilers that will be necessary.

**Standard**

If not using -ansi which will default to c89 or c99

`-std=c23`

Unneccessary feature disabling/portability, entering c89 or c99 mode

`-pedantic -ansi`

**Optimizations**

`-O2`

**Static analysis**

`-fanalyzer`

**Warnings**

```-Wall -Wextra -Wpedantic -Wformat=2 -Wformat-overflow=2 -Wformat-truncation=2 -Wformat-security \
-Wnull-dereference -Wstack-protector -Wtrampolines -Walloca -Wvla -Warray-bounds=2 \
-Wimplicit-fallthrough=3 -Wtraditional-conversion -Wshift-overflow=2 -Wcast-qual \
-Wstringop-overflow=4 -Wconversion -Warith-conversion -Wlogical-op -Wduplicated-cond \
-Wduplicated-branches -Wformat-signedness -Wshadow -Wstrict-overflow=4 -Wundef \
-Wstrict-prototypes -Wswitch-default -Wswitch-enum -Wstack-usage=1000000 -Wcast-align=strict
```

`-Werror` on local builds, disable on CI

**Debug/testing**

```
-DDEBUG -ggdb -fsanitize=address -fsanitize=pointer-compare -fsanitize=pointer-subtract -fsanitize=leak -fno-omit-frame-pointer -fsanitize=undefined -fsanitize=bounds-strict -fsanitize=float-divide-by-zero -fsanitize=float-cast-overflow
```

If application is multi-threaded, use the following (not compatible with ASAN):

`-fsanitize=thread`

**Security**

Glibc

`-D_FORTIFY_SOURCE=3`

Additional features for ASLR/stacks and traps

`-fstack-protector-strong -fstack-clash-protection -fPIE -fsanitize=bounds -fsanitize-undefined-trap-on-error`

Linker options

`-Wl,-z,relro -Wl,-z,now -Wl,-z,noexecstack -Wl,-z,separate-code`

Enable ASAN for non-threaded code

`export ASAN_OPTIONS=strict_string_checks=1:detect_stack_use_after_return=1:check_initialization_order=1:strict_init_order=1:detect_invalid_pointer_pairs=2`

Spectre-specific

`-mfunction-return -mindirect-branch-register -mindirect-branch=thunk-extern`

## References

- [airbus-seclab's c-compiler-security](https://github.com/airbus-seclab/c-compiler-security)
