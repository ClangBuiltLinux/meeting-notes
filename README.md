# Clang-Built Linux Meeting Notes

Notes from our meeting every other week. See
[our homepage](https://clangbuiltlinux.github.io/) for links to the calendar
invite and meet link.

Send to: llvm@lists.linux.dev

## Oct 6, 2021
- Meeting notes moved to github
- [Meetup in Oct](https://www.eventbrite.com/e/bay-area-llvm-developers-meetup-tickets-173682136947)
- (Nick): Working on https://github.com/ClangBuiltLinux/linux/issues/1302 in LLVM.
- BLK_DEV_NBD issue all resolved https://github.com/ClangBuiltLinux/linux/issues/1438
- (Serge, Nick): small fixes for inline https://goto.google.com/llvm-cr/D111009, https://goto.google.com/llvm-cr/D107872
- Collabora blog post on glibc+llvm:
  - https://www.collabora.com/news-and-blog/blog/2021/09/30/a-tale-of-two-toolchains-and-glibc/
  - "Glibc built by LLVM should be achievable if we consider the successful effort to add first-class Clang support to the Linux kernel which is also a complex and historically tied-to GCC project." "Even without a big concentrated effort like the Linux kernel had..."
  - https://sourceware.org/bugzilla/show_bug.cgi?id=28376
- (Nick) thumb2 boot failure in qemu 6.1.0+ fix: https://lore.kernel.org/llvm/20210929190810.1597399-1-ndesaulniers@google.com/
- (Kees, Nathan) CI problem matcher updates:
  - https://github.com/ClangBuiltLinux/continuous-integration2/pull/211
  - https://github.com/ClangBuiltLinux/continuous-integration2/pull/215
- exponential backoff
- (Sami) CFI x86 v4: https://lore.kernel.org/lkml/20210930180531.1190642-1-samitolvanen@google.com/
- kselftests broken
- muloti4
  - should disable for linux (not android, cros?) and windows (not cygwin)
  - https://bugs.llvm.org/show_bug.cgi?id=52043
- -Wframe-larger-than= discussion
  - why does GCC use less stack than Clang with the same KASAN features enabled?
  - dynamic tools team saying not a bug
  - Can we limit inlining for kasan?
  - Can we disable -Wframe-larger-than= for KASAN_STACK?
  - Minimize the warnings from allmodconfig/allyesconfig
  - Avoiding disabling KASAN_STACK w/ clang.
  - Too much padding between objects in KASAN_STACK w/ clang?
  - Can we tune the inline cost model for KASAN (not ASAN)?
  - TBD next week; Arnd to pull a few interesting use cases (very high stack useage) from all\*configs, Marco, Glider, and Nick to analyzer a few individual cases.


## Sep 22, 2021
Bill describing difficulties in implementation of zeroing callee used regs.
Plumbers (Toolchain MC Friday)
Almost back to green in CI now that we can apply patch files
TODO: re-enable -Werror for allmodconfig builds
Arnd’s randconfig W=1 builds almost green for GCC and Clang
https://git.kernel.org/pub/scm/linux/kernel/git/arnd/playground.git/log/?h=randconfig-5.15-min 
Kees had QEMU buffering fixes for ci
Nick bootstrapping llvm against musl
https://reviews.llvm.org/D109837
Try -DLLVM_HOST_TRIPLE=


## Sep 8, 2021
Need attribute error warning kernel fixes to be picked up by Miguel
https://github.com/ClangBuiltLinux/linux/issues/1173 
__mulodi4 llvm fixes in, need to do kernel fixes
https://github.com/ClangBuiltLinux/linux/issues/1438 
Todo file bug against gcc for mulodi4?
Switch bit test fixes landed in llvm fixes LTO boot
https://reviews.llvm.org/rG4331f19d8b9ac8101d55073834b35814afce4e5a 
-Werror
https://lore.kernel.org/lkml/20210907183843.33028-1-ndesaulniers@google.com/ 
Sanitizer vs frame-larger-than=
Stable vs compiler version checks
TODO Disable WERROR in CI
LLVM_IAS=1 CROSS_COMPILE landed in mainline
5.15 merge window open 
Conf cfps
Distributors conf: https://github.com/ClangBuiltLinux/llvm-distributors-conf-2021/issues 
CBL meetup 2: https://github.com/ClangBuiltLinux/CBL-meetup-II-turbo/issues 
LinuxConfAU extended their deadline: https://linux.conf.au/programme/miniconfs/ 
LLVM virtual meetup (no BoFs this year, let's do a roundtable?): https://lists.llvm.org/pipermail/llvm-dev/2021-September/152483.html 
Kasan s390 ci coverage added to our CI
Nearing Github Actions CI matrix limit
Kees fortify patches (being split into 2 series)
New mailing list and IRC
TODO update mailmap
llvm@lists.linux.dev
 #clangbuiltlinux on irc.libera.chat
Sami CFI patches
https://reviews.llvm.org/D108478
https://reviews.llvm.org/D108479
Bill finding shadowing and scev issues (b/198158061) (https://reviews.llvm.org/D104741)
Talk to Miguel if you’re interested in Rust+kernel
(Nick) tailcall optimizations for fortified routines: https://reviews.llvm.org/D107872 

## Aug 25, 2021
Error+warning attributes landed
https://reviews.llvm.org/D106030
30 years of Linux!
https://lwn.net/Articles/867315/
-Wimplicit-fallthrough for 5.15?
https://github.com/ClangBuiltLinux/linux/issues/1429
https://github.com/llvm/llvm-project/commit/9ed4a94d6451046a51ef393cd62f00710820a7e8
https://lore.kernel.org/r/20210819040517.GA329693@embeddedor/
ThinLTO regression in LLVM
https://github.com/ClangBuiltLinux/linux/issues/1440
https://reviews.llvm.org/D106056
https://lore.kernel.org/r/5913cdf4-9c8e-38f8-8914-d3b8a3565d73@kernel.org/
CFI x86_64 v2 series
https://lore.kernel.org/r/20210823171318.2801096-1-samitolvanen@google.com
Currently limited to clang-14 but compiler side fix should be going in clang-13.
-falign-jumps=0 warning
https://lore.kernel.org/r/202108210311.CBtcgoUL-lkp@intel.com/
https://lore.kernel.org/r/20210824022640.2170859-1-nathan@kernel.org/
https://lore.kernel.org/r/20210824232237.2085342-1-nathan@kernel.org/
clang-13 and sanitizer coverage in CI merged
https://github.com/ClangBuiltLinux/continuous-integration2/pull/178
https://github.com/ClangBuiltLinux/continuous-integration2/pull/179
cc-option-yn removal
https://lore.kernel.org/r/20210817002109.2736222-1-ndesaulniers@google.com/
-Wbool-operation enhancement
https://reviews.llvm.org/D108003
PowerPC '-z notext' fix for CONFIG_RELOCATABLE
https://lore.kernel.org/r/20210812204951.1551782-1-morbo@google.com/
Getting help from Intel on certain bugs
https://groups.google.com/g/clang-built-linux/c/fIy6K5Uxr3s/m/vV--Yt78BgAJ
llvm@lists.linux.dev
https://subspace.kernel.org/lists.linux.dev.html
https://subspace.kernel.org/#subscribing
LTO kbuild patches
https://lore.kernel.org/lkml/CAK7LNARoxA875uynQHs-HpcfXtzFvuxkzSha9tquR2uV0Za10A@mail.gmail.com/ 
Fortify source series for 5.15 then 5.16?
Bill looking into zero call registers

## Aug 11, 2021
ARMv4 LLD support discussion `--fix-v4bx`
https://bugs.llvm.org/show_bug.cgi?id=51422 
cc-option-yn necessary?
https://groups.google.com/g/clang-built-linux/c/PL9lE_eKhhs 
https://github.com/ClangBuiltLinux/linux/issues/1436 
https://lore.kernel.org/lkml/20210811175647.3851629-1-ndesaulniers@google.com/ 
https://lore.kernel.org/lkml/20210810204240.4008685-1-ndesaulniers@google.com/ 
Blog Posts
Funded open source security work at the Linux Foundation
https://linuxfoundation.org/blog/funded-open-source-security-work-at-the-linux-foundation/ 
Linux Kernel Security Done Right
https://security.googleblog.com/2021/08/linux-kernel-security-done-right.html 
Oops! Can’t require LLD for Android R…
https://android-review.googlesource.com/c/platform/test/vts-testcase/kernel/+/1789650/ 
Death to CROSS_COMPILE
https://lore.kernel.org/lkml/20210802183910.1802120-1-ndesaulniers@google.com/ 
https://github.com/ClangBuiltLinux/linux/issues/1399 
Death to LLVM_IAS=1
https://lore.kernel.org/lkml/20210805150102.131008-1-masahiroy@kernel.org/ 
https://lore.kernel.org/lkml/20210806172701.3993843-1-ndesaulniers@google.com/ 
https://github.com/ClangBuiltLinux/linux/issues/1434 
https://github.com/ClangBuiltLinux/continuous-integration2/pull/181 
__attribute__((error(“”))) __attribute__((warning(“”))) (Nick) for BUILD_BUG and friends
https://lore.kernel.org/lkml/20210802202326.1817503-1-ndesaulniers@google.com/ 
https://reviews.llvm.org/D107613 
https://reviews.llvm.org/D106030 (WIP)
Distro configs now in CI (Fedora, Suse, Arch)
https://github.com/ClangBuiltLinux/continuous-integration2/pull/172 
CFI fix for inline asm references to static functions
https://reviews.llvm.org/D104058 
https://github.com/ClangBuiltLinux/linux/issues/1354 
LLVM13 CI coverage WIP
https://github.com/ClangBuiltLinux/continuous-integration2/pull/179 
Sanitizer build+boot CI coverage WIP
https://github.com/ClangBuiltLinux/continuous-integration2/pull/178 
CFI remove __typeid__ symbols from JT to aid debugging (Nick)
ASAN ctor/dtor needed to boot test aarch64
https://lore.kernel.org/linux-arch/20210731023107.1932981-1-nathan@kernel.org/ 
__builtin_object_size questions (Kees)
How to determine if something is a flexible array member?
int foo [0]; // no size, just a marker/symbol that’s addressable
int foo []; // flexible array member, malloc + additional size
Why can’t flex arrays be in union, or alone in anonymous struct?
https://git.kernel.org/pub/scm/linux/kernel/git/kees/linux.git/commit/?h=kspp/memcpy/next-20210803/v2-devel&id=8725f84346c1be20ccb21aedb3e46f25e3ab9f3a 
https://git.kernel.org/pub/scm/linux/kernel/git/kees/linux.git/commit/?h=kspp/memcpy/next-20210803/v2-devel&id=0f28d9daf643a1110bc7536f590e60035ba17635 

## July 28, 2021
Fortify Source (Kees)
https://lore.kernel.org/lkml/20210727205855.411487-1-keescook@chromium.org/ 
Phoronix benchmarked LTO
https://www.phoronix.com/scan.php?page=article&item=clang-lto-kernel&num=1 
Intel 0 day bot now running clang static analyzer continuously
https://groups.google.com/g/clang-built-linux/c/NY64cegnl8o 
https://groups.google.com/g/clang-built-linux/c/0Kn8V3wI-Jo 
RISCV + LTO patches sent
https://lore.kernel.org/linux-riscv/20210719205339.1023572-1-twd2.me@gmail.com/ 
https://lore.kernel.org/linux-riscv/20210719205247.1023289-1-twd2.me@gmail.com/ 
https://lore.kernel.org/linux-riscv/20210719205314.1023455-1-twd2.me@gmail.com/ 
Attr Error + Warning (Nick) WIP: https://reviews.llvm.org/D106030 
TODO (Nick): send v3 of CROSS_COMPILE
TODO (Nick): Nathan had feedback on one patch __error__
LLVM14 to branch
Max TCWG IRC libaro #linaro-tcwg on libera.chat
Static analysis https://lore.kernel.org/ksummit/20210723191023.GG25548@kadam/ 
Sept 21 tentative clang-13 ship

## July 14, 2021
Death to CROSS_COMPILE!
https://lore.kernel.org/lkml/20210708232522.3118208-1-ndesaulniers@google.com/ 
Death to LLVM_IAS=1
Mips can now be built with LLVM_IAS=1
https://lore.kernel.org/lkml/20210628215029.2722537-1-ndesaulniers@google.com/ 
Ppc and s390 left
?=
RISCV
LOCAL
https://reviews.llvm.org/D105720 
https://sourceware.org/binutils/docs/as/Altmacro.html 
https://lore.kernel.org/linux-riscv/CAKwvOdm65wmFQE6_wkVFFE6us99xXoqS8E-qORX9XmsD2uJ1dQ@mail.gmail.com/
VDSO
https://lore.kernel.org/lkml/20210707185105.1180526-1-abdulras@google.com/ 
(Nick) __attribute__((error(“”))) __attribute__((warning(“”)))
ThinLTO inline asm
https://reviews.llvm.org/D104058
Hexagon allyesconfig almost ready
https://lore.kernel.org/lkml/20210708233849.3140194-1-nathan@kernel.org/ 
Linaro Connect CFP
Rust support? LLVM?
Fallthrough edge case
https://github.com/ClangBuiltLinux/linux/issues/1429 
Abigail complex types

## June 30, 2021
PGO on the rocks
https://lore.kernel.org/lkml/CAHk-=whqCT0BeqBQhW8D-YoLLgp_eFY=8Y=9ieREM5xx0ef08w@mail.gmail.com/ 
Should be able to enable LLVM_IAS=1 on mips soon:
https://lore.kernel.org/lkml/20210628215029.2722537-1-ndesaulniers@google.com/T/#u 
Still some warnings
Should we flip LLVM_IAS=1 to on when LLVM=1?
PPC
S390
Toolchain MC has been accepted at plumbers
https://www.linuxplumbersconf.org/blog/2021/index.php/2021/06/21/toolchains-and-kernel-microconference-accepted-into-2021-linux-plumbers-conference/ 
More Nest devices switching to clang built kernels
Leaving freenode IRC
Send LLVM Revert Checker tool to Tom
https://cs.android.com/android/platform/superproject/+/master:external/toolchain-utils/llvm_tools/revert_checker.py 
Fortify source (Kees)
-Wrestrict (Kees, Arnd)
We can build more 32b ARM? Should we add more to CI?
https://tinyurl.com/linux-architectures

## June 16, 2021
RISCV
https://reviews.llvm.org/D103539 
LTO
https://reviews.llvm.org/D104342 
PGO
https://reviews.llvm.org/D104253
(GCOV) https://reviews.llvm.org/D104257 
Bunch of objtool fixes last week (3)
https://www.phoronix.com/scan.php?page=news_item&px=Clang-PGO-For-Linux-Next 
Working through last minute approvals for plumbers MC
Started discussion internally about “hardware for hackers”
Distributors conf & CBL meetup 2
https://lists.llvm.org/pipermail/llvm-dev/2021-March/149234.html 
 #clang-built-linux on LLVM Discord


## June 2, 2021
Planning second meetup: Friday September 17 2021
Planning LLVM Distributors Conf: Thursday September 16 2021
Series of fixes for PGO being posted
(Nathan) fixes for Hexagon
https://lore.kernel.org/lkml/20210521011239.1332345-1-nathan@kernel.org/ 
Riscv boot failure
https://github.com/ClangBuiltLinux/linux/issues/1389 
Strange PGO failure
https://github.com/ClangBuiltLinux/linux/issues/1388 
(Nathan) PPC breakage
https://github.com/ClangBuiltLinux/linux/issues/1386 
Upstream regression reverted (worth chasing a reproducer?)
https://github.com/ClangBuiltLinux/linux/issues/1385 
CFI boot failure on WSL2
https://github.com/ClangBuiltLinux/linux/issues/1384 
(Nick) PGO crash (will ask upstream LLVM to revert)
https://github.com/ClangBuiltLinux/linux/issues/1383 
M68k making progress
https://github.com/ClangBuiltLinux/linux/issues/1387 
(Nick) still looking into section mismatch warnings
https://github.com/ClangBuiltLinux/linux/issues/1302 
commit 4a3893d069b7 ("modpost: don't emit section mismatch warnings for compiler optimizations")
(Nick) Reverting android patches for -fuse-ld=lld and -rtlib=compiler-rt
https://github.com/ClangBuiltLinux/linux/issues/479 
(Jian) -Wa,-march
(Bill) KASAN KVM crashes, potentially a fix on llvm to backport to 12.0.1 release
(Tom) June 8 tentative cutoff date for clang 12.0.1
(Gustavo) -Wimplicit-fallthrough down to ~25 patches on -next
https://redshirtjeff.com/listing/linux-recompile-shirt?product=211 

## May 19, 2021
(Nick) Per task stack canaries on arm64 (broke LTO)
https://reviews.llvm.org/D102742 
(Nick) __builtin_constant_p fix for flexible arrays
https://reviews.llvm.org/D102367 
(Nick) removing GAS from Android kernels
(Nathan) AMDGPU LTO fix
(Nathan) problem matchers in github actions now!
M68k backend has inline asm support
https://reviews.llvm.org/D102585
No san cov attr
https://reviews.llvm.org/D102772 
Arnd
https://lore.kernel.org/lkml/20210514100106.3404011-1-arnd@kernel.org/ 
Randconfig turning off COMPILE_TEST is problematic (0day bot)
Can we move some checks from sparse into clang proper? (or clang-tidy)
Broonie
LTP build w/ clang recently failed
https://release.debian.org/bullseye/arch_policy.html Debian’s arch policy
Tstellar
Rebuilding parts of Fedora with Clang
Fangrui:
https://maskray.me/blog/2021-05-16-elf-interposition-and-bsymbolic#the-last-alliance-of-elf-and-men 

## May 5, 2021
Bug scrub burned down ⅓ of bugs!
Aarch64 full LTO boot failure fixed
https://github.com/ClangBuiltLinux/linux/issues/1368 
Issues with LTO+TRIM_UNUSED_KSYMS
https://github.com/ClangBuiltLinux/linux/issues/1369 
S390 allmodconfig build failures
https://github.com/ClangBuiltLinux/linux/issues/1370 
New warnings from opening merge window
ARCH=hexagon support imminent
https://groups.google.com/g/clang-built-linux/c/OvG71CL1KWc/m/MUBfBmCJAwAJ 
Aarch64 per task stack canaries (Nick): https://reviews.llvm.org/D100919 
Alignment issue for blk has a fix, needs a v2
https://lore.kernel.org/lkml/20210429150940.3256656-1-arnd@kernel.org/ 
Plumbers is virtual Sept 20-24
https://www.linuxplumbersconf.org/blog/2021/ 
Arnd mentioned this gcc bug report:
https://gcc.gnu.org/bugzilla/show_bug.cgi?id=100363
I agree with the GCC maintainers that use of underaligned pointers is undefined behavior.
https://trust-in-soft.com/blog/2020/04/06/gcc-always-assumes-aligned-pointer-accesses/ is an interesting read linked from the gcc bug report.

## April 21, 2021
Ppc32 boot failures
https://github.com/ClangBuiltLinux/linux/issues/1345#issuecomment-816864777 
Debian LLVM patches causing issues
https://github.com/ClangBuiltLinux/linux/issues/1355 
Gcov shenanigans
https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=7af08140979a6e7e12b78c93b8625c8d25b084e2 
KCOV issues resolved
CFI feedback
Aarch64 per task stack canaries (Nick): https://reviews.llvm.org/D100919 
Alignment issue in blk still not resolved
https://github.com/ClangBuiltLinux/linux/issues/1328 
Double CI, oops!
Fortify source
Merge window opening
Bug scrub tomorrow!


## April 7, 2021
KCOV broken for CFI (Nick)
Missing debug info, but __sanitizer_cov_trace_pc should probably also be __noinline.
https://github.com/ClangBuiltLinux/linux/issues/1338 
Working on 2 fixes for LLVM.
GCOV broken in clang-11+ (Nick)
https://lore.kernel.org/lkml/20210407185456.41943-1-ndesaulniers@google.com/ 
Arm32 IAS patch (Jian)
https://reviews.llvm.org/D98916 
Pahole patches
https://lore.kernel.org/dwarves/YG3SYoNWqb8DlP61@kernel.org/ 
RISC-V
https://github.com/riscv/riscv-elf-psabi-doc/issues/183 R_RISCV_ALIGN
Alignment issue in blk
https://github.com/ClangBuiltLinux/linux/issues/1328
Plumbers
Submitted MC proposal for “Toolchains and Kernel MC” with Jose Marchesi from Oracle’s GCC team.
Drop clang-10 support?
Clang-12 maybe released next week?
Can next debian still include clang-10 for kernel builds?
Can tuxsuite fetch clang-10 from apt.llvm.org for now?
CFI needs help testing
V5: https://lore.kernel.org/lkml/20210401233216.2540591-1-samitolvanen@google.com/ 
Gcc implemented support for asm goto w/ outputs! W00t
https://gcc.gnu.org/git/gitweb.cgi?p=gcc.git;h=e3b3b59683c1 
Compare_exchange
https://godbolt.org/ 
https://lore.kernel.org/lkml/YG2fQ1tGDIMhyIHe@hirez.programming.kicks-ass.net/ 
Building perf with clang has some issues

## March 24, 2021
LLVM_IAS=1 ARCH=arm landing in Android
Probably going to skip 4.19.y, one last assembler bug won't be ready in time, 27 kernel backports required.
https://reviews.llvm.org/D98916 
https://lore.kernel.org/stable/be846d89-ab5a-f02a-c05e-1cd40acc5baa@roeck-us.net/ 
https://lore.kernel.org/stable/CAKwvOdm6FXWVu-9YkQNNyoYmw+hkj1a7MQrRbWyUxsO2vDcnQA@mail.gmail.com/ 
32b PPC BE builds spun down in CI
https://github.com/ClangBuiltLinux/continuous-integration2/pull/111 
https://github.com/ClangBuiltLinux/linux/issues/1292 
https://bugs.llvm.org/show_bug.cgi?id=49610 
Riscv crash on -next, requires earlycon to get more info (or GDB)
CFI patches need help review+test
V3: https://lore.kernel.org/lkml/20210323203946.2159693-1-samitolvanen@google.com/ 
PGO patches need help review+test
https://lore.kernel.org/lkml/20210226222030.3718075-1-morbo@google.com/ 
Wenlei, Hongtao, Yonghong (ThinLTO+pahole)
https://reviews.llvm.org/D80765 
Duplicate type info, skip emitting it for cross TU defined types? (TODO: Nick: talk with dblaikie@)
Inlining of global functions means they can’t be traced; __no_inline_for_lto __attribute__((noinline))? Prevent inlining in LLVM?
Rémi, Antonio
TuxTest, TuxRun demo
https://gitlab.com/Linaro/tuxsuite#tuxtest TuxRun not yet ready, stay tuned
Would allow us to drop distributing QEMU, simplify workers in CI
Plan file support to be added to tuxsuite, months out though
(Arnd) warning promotions
Warnings were disabled in top level Makefile, but not enable-able via W=123
j
## March 10, 2021
Integrated as
(Nick) working on enabling for arm in Android.
Will do another pass for THUMB2.
32b ARM boot failures CrOS .text.unlikely.
https://bugs.chromium.org/p/chromium/issues/detail?id=1184483 
LTO crashes
Try disabling CONFIG_SYSCTL_SYSCALL 
Next is red? (unrelated)
Ipsccp
https://reviews.llvm.org/D97971 
kernelci 
Spin down clang-11 builds?
SGTM
Compile times with sanitizers
https://bugs.llvm.org/show_bug.cgi?id=38809#c16
https://github.com/ClangBuiltLinux/linux/issues/1314 
Arnd ran some stats: https://docs.google.com/spreadsheets/d/1EoKc3ploXakwVHx_Pz8D5-1fMU2xiJHLiySvaeJpBgk/edit#gid=0 

## Feb 24, 2021
Integrated as (THUMB2)
Final blocker to build: https://github.com/ClangBuiltLinux/linux/issues/1286 
LTO has landed upstream!
Arm64: https://lore.kernel.org/lkml/CAHk-=wgQ=oaLD_ybzhOP+8LFNZH3Qzpc-dp4XB4cXxXLReCdnQ@mail.gmail.com/ 
X86_64: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=414eece95b98b209cef0f49cfcac108fd00b8ced 
BTF support?
Curious inlining changes from NPM (ipsccp)
https://github.com/ClangBuiltLinux/linux/issues/1302 
Using qemu from ubuntu for riscv
https://github.com/ClangBuiltLinux/linux/issues/1293 causing x86_64 allmodconfig to fail to build w/ clang-10.  Can’t fix clang-10.  Turn down build or bump minor version?
Kconfig depends on clang-11+
https://lore.kernel.org/lkml/c0ff7dba14041c7e5d1cae5d4df052f03759bef3.1613243844.git.luto@kernel.org/ missing stack protector for 32b x86: https://bugs.llvm.org/show_bug.cgi?id=49209 
Kpatch clang support: https://github.com/dynup/kpatch/pull/1156 
Boot test Debian images: https://github.com/ClangBuiltLinux/boot-utils/pull/35 
http://cdn.kernel.org/pub/linux/kernel/people/will/docs/qemu/qemu-arm64-howto.html 


https://github.com/ClangBuiltLinux/linux/issues/1269 LTO issue blocking toolchain upgrades
ETM related arm64 IAS
Rust for linux: https://github.com/Rust-for-Linux/linux/issues 
Testers wanted:
PGO:
Polly:

## Feb 10, 2021
Integrated as
Arm32 patches
https://reviews.llvm.org/D95872 
https://reviews.llvm.org/D96285 
https://reviews.llvm.org/D96304 
Arnd filed a ton of bugs via randconfigs
Need https://lore.kernel.org/linux-arm-kernel/20210205223557.3097894-1-ndesaulniers@google.com/T/#u reviewed.
0day bot GCC report
X86 (64b & 32b) and aarch64 enabled for Android S 4.19+, CrOS 5.4+
(Bill) pahole + LTO
Different stack sizes objtool
https://github.com/ClangBuiltLinux/linux/issues/612 
(Nick) DWARFv5
https://lore.kernel.org/bpf/20210207071726.3969978-1-yhs@fb.com/ BTF fix
V9 is probably final version: https://lore.kernel.org/lkml/20210205202220.2748551-1-ndesaulniers@google.com/ 
Requires integrated assembler for old GNU binutils.
LLD BE support!
https://lore.kernel.org/lkml/20210209005719.803608-1-nathan@kernel.org/T/#u 
32b ARM, s390, ppc?
Mips be enable
https://youtu.be/GpiWVXKs9Z0 : "ClangBuiltLinux: What's Next?" - Nick Desaulniers (LCA 2021 Online)
32b ARM LLD bug fixed
https://lore.kernel.org/linux-arm-kernel/20210205085220.31232-1-ardb@kernel.org/T/#u 
vfs_truncate BTF BTI
https://github.com/ClangBuiltLinux/linux/issues/1297 
NPM causing one issue for ppc, -Werror though
https://github.com/ClangBuiltLinux/linux/issues/1292 
Tuxsuite working well, adding many tests
PGO? (needs chasing upstream)
Inlining kasan experiment 
Mailing list?

## Jan 27, 2021
Integrated as
Reverted for x86_64 for 4.19 due to ltp nanosleep 32b test
https://android-review.googlesource.com/c/kernel/common/+/1559459 
Arm32b blocked on https://github.com/ClangBuiltLinux/linux/issues/1195, https://bugs.llvm.org/show_bug.cgi?id=48894. 
LTO bugs
Debug info growth out of control
thinLTO duplicates CU entries
New objtool series for x86
https://lore.kernel.org/lkml/cover.1611263461.git.jpoimboe@redhat.com/ 
PGO bugs
https://lore.kernel.org/lkml/20210122101156.3257143-1-morbo@google.com/ 
Reported issues with hash mismatches?
-Wno-error=backend-plugin
Dwarfv5???
CI work
https://github.com/ClangBuiltLinux/continuous-integration2
https://gitlab.com/cki-project/pipeline-definition/-/merge_requests/1085 
LinuxConfAU report
Slides: https://lca-kernel.ozlabs.org/2021-Desaulniers-ClangBuiltLinux_Whats_Next.pdf 
Parsing bug Linus+Will
https://reviews.llvm.org/D95408 
Fixed infinite loop observed on s390 build
https://goto.google.com/llvm-cr/D94996 
Ubsan bug_on (need to chase these) allmodconfig failures
llvm 10 and llvm11 next
https://github.com/ClangBuiltLinux/continuous-integration2/issues/58 
https://github.com/ClangBuiltLinux/continuous-integration2/issues/57 
-Wunreachable-code-*
https://github.com/ClangBuiltLinux/linux/issues/1180 
Objtool arm64
Requires a GCC plugin?
https://lore.kernel.org/lkml/a3393eb3-03a5-e4dd-f40c-b801cc60778e@linux.microsoft.com/T/#m44b90dc4ff63f86e76ac4ee68710dfe61b69720e 

## Jan 11, 2021
PGO patch: https://lore.kernel.org/lkml/20210113061958.886723-1-morbo@google.com/  
Regressions!
Arm: https://lore.kernel.org/stable/20210113185758.GA571703@ubuntu-m3-large-x86/T/#u 
Modules: https://github.com/ClangBuiltLinux/linux/issues/1250 
Ubsan: https://github.com/ClangBuiltLinux/linux/issues?q=is%3Aissue+is%3Aopen+UBSAN 
CI back online
https://github.com/ClangBuiltLinux/continuous-integration2 
CKI: https://gitlab.com/cki-project/pipeline-definition/-/issues/1 
Linuxconf au
Thoughts on mixing matching + still supporting CC=clang even after moves to LLVM=1.
https://linux.conf.au/schedule/presentation/107/ 
Dwarf5
https://lore.kernel.org/lkml/20210113003235.716547-1-ndesaulniers@google.com/ 
LLVM_IAS=1 enabled for 4.19+ for aarch64 in android.
Objtool IAS issue: https://github.com/ClangBuiltLinux/linux/issues?q=is%3Aissue+is%3Aopen+label%3A%22%5BTOOL%5D+objtool%22+label%3A%22%5BTOOL%5D+integrated-as%22 
Llvm-objcopy cros
Gentoo build system runs as root
https://reviews.llvm.org/D93881 
Polly
https://github.com/lazerl0rd/tryme_redbull/commit/c2da3277cc0143c1351b9e49f15e918041c9aef1 
Reliable stack traces for arm64
Objtool: https://lore.kernel.org/linux-arm-kernel/20200109160300.26150-1-jthierry@redhat.com/ 
32b LLVM_IAS=1 arm
Likely usual issues with CC=clang and ARMv4
S390
Looking great, just need qemu fixes to get merged and packaged.
History tree: https://git.kernel.org/pub/scm/linux/kernel/git/tglx/history.git/ 
“Clang LTO Support Looks Like It Could Land For Linux 5.12”: https://www.phoronix.com/scan.php?page=news_item&px=Clang-LTO-Linux-Next-Queue 

## Dec 16, 2020
https://lwn.net/Articles/838807/
https://meet.google.com/linkredirect?authuser=0&dest=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2F1QxMvW5jpVG2jb4RM9CQQl27-wVpNYOa-_3K2RVKifb0%2Fedit%23gid%3D596881437 


## Dec 1, 2020
LLVM_IAS=1
.ascii directive almost ready to land https://reviews.llvm.org/D91460 
Issue unwinding possibly due to ARMv8.3 PAC?
LTO v8 patches need help testing https://lore.kernel.org/lkml/20201201213707.541432-1-samitolvanen@google.com/ 
KernelCI reports are back now that orphan section warnings are fixed.
ld --cref, ClangBuildAnalyzer for dependency tracking
https://github.com/aras-p/ClangBuildAnalyzer 
Arnd’s header changes speed up Clang builds significantly more than GCC builds. Needs to be rebased.
Tuxbuild github action demo: https://github.com/danrue/tuxbuild-demo 
Tuxbuild testing sparc tinyconfig
Arnd recommends only focus on sparc64, not sparc32.
Nick emailed TravisCI about builds being offline since Nov 20.
%hh treewide cleanups for -Wformat. Clang-tidy for treewide cleanups?
https://github.com/ClangBuiltLinux/linux/issues/378#issuecomment-737539378 
TODO(Nick): update DWARFv5 patches
Linaro Connect ‘21 March 23 virtual https://connect.linaro.org/cfp/ 

## Nov 18, 2020
Orphan Section Warning patches up for lld-10. https://github.com/ClangBuiltLinux/linux/issues/1187 
LLVM_IAS=1
IWMMXT arm32 LLVM_IAS=1 patch submitted. https://github.com/ClangBuiltLinux/linux/issues/975 
-Wa,-march=armv7-a issue https://github.com/ClangBuiltLinux/linux/issues/1195 
.ascii directive issue https://github.com/ClangBuiltLinux/linux/issues/1196 
Bill sending PPC LLVM_IAS=1 patches https://lore.kernel.org/linuxppc-dev/20201017004752.415054-1-morbo@google.com/ 
Stack protector LTO inlining bug affecting x86 suspend/resume. https://bugs.llvm.org/show_bug.cgi?id=47479 
barrier_data fallout still landing; needs backports. https://github.com/ClangBuiltLinux/linux/issues/1202 
Android kernels updated; minor LTO related regression for 4.19 from unmerged sections. https://android-review.googlesource.com/c/kernel/common/+/1511434 
-Wimplicit-fallthrough LKML discussions https://lore.kernel.org/lkml/cover.1605896059.git.gustavoars@kernel.org/ 
-Wformat LKML discussions https://lore.kernel.org/lkml/26052c5a0a098aa7d9c0c8a1d39cc4a8f7915dd2.camel@perches.com/ 
CI: gitlab pipelines vs github actions

## Nov 4, 2020
Tom Rix clang-tidy for tree wide fixits
https://reviews.llvm.org/D90180 
Prodkernel rollout underway
DWARF5 WIP
https://lore.kernel.org/lkml/20201104005343.4192504-1-ndesaulniers@google.com/T/#u 
Pixel tracing issue
https://lore.kernel.org/lkml/20180725202238.165314-1-salyzyn@android.com/ 
Re-fixing again now via SELinux
Pixel upgrading clang version
-Wvoid-pointer-to-int-cast
SYM_FUNC_START_WEAK integrated assembler breakage.
https://lore.kernel.org/stable/20201103012358.168682-1-maskray@google.com/ 
^ x86_64 specific. There’s another patch already in mainline for arm64, and another sent for perf.
Stack protector
https://reviews.llvm.org/D90194
https://reviews.llvm.org/D90348
https://reviews.llvm.org/D90353 
LLD offset bug
https://reviews.llvm.org/D90520 
IWMMXT
https://sourceware.org/legacy-ml/binutils/2006-07/msg00324.html
http://read.pudn.com/downloads78/ebook/297953/WirlessMMX251669_devguide.pdf 
CrOS thumb fp unwind bug (userspace specific)
GKH bug report related to io_vec
https://lore.kernel.org/lkml/20201102135202.GA1016272@kroah.com/ 
Probably not the last we’ve seen of this bug
Kees is streaming on twitch!
https://www.twitch.tv/keescook/about 
https://www.youtube.com/channel/UC6zmTkbgwe2q6l6TNjABSCg 

## Oct 21, 2020
Android common kernels have moved to LLVM=1, GNU binutils (modulo GAS) removed.
LLVM_IAS=1 is next, CrOS has similar patch staged (but CrOS is still using the rest of GNU binutils).
-gdwarf-2 warnings
Fixing aarch64 compat vdso hardcoding ld.bfd was a big help.
Android toolchain upgrade is causing CTS failures for bionic.
Working on a fix for -fstack-protector and LTO: https://reviews.llvm.org/D87956 
Clang-11 released!
KernelCI upgrading now.
KSelftests hard coding GCC?
We might need to upgrade our CI once clang-12 branch is created.
Internal report that LLD is corrupting data in .bss due to ALIGN statements.
S390 buildroot minor release not good enough, need to wait for next release in November.
LinuxConfAU CFP: https://lwn.net/Articles/834440/ 
LLVM Dev Conf is a wrap
barrier_data bug: https://lore.kernel.org/lkml/20201014212631.207844-1-nivedita@alum.mit.edu/T/#u 
Twitch Stream?
Fix -Wformat
`-Wunreachable-code-loop-increment`, `-Wunreachable-code-break`, and
`-Wunreachable-code-return`
Userspace
W=123 warnings
Build bug on sucks: https://github.com/ClangBuiltLinux/linux/issues/1173 
Fortify source (Kees)


## Sep 23, 2020
CrOS boot failure in 4.4 fixed just in time for clang-11. Thanks Jian and James!
https://bugs.chromium.org/p/chromium/issues/detail?id=1123683 
https://reviews.llvm.org/rGf7a53d82c0902147909f28a9295a9d00b4b27d38 
https://bugs.llvm.org/show_bug.cgi?id=47468 
LLVM=1 (Nick) in Android
KernelCI moved over
Binutils for Android kernel deprecation schedule: https://android-review.googlesource.com/c/platform/prebuilts/clang/host/linux-x86/+/1405387 
Backported to 5.4, Working on backport to 4.19
(Mark): can we even eliminate LLVM=1?
Syzbot stray 4B write
https://groups.google.com/g/clang-built-linux/c/b4Obxq5w6hw 
S390 buildroot support being added, should be able to boot test s390 soon
https://github.com/ClangBuiltLinux/continuous-integration/issues/232#issuecomment-693255238 
Llvm dev conf coming up, anyone want to moderate my session?
LTO stack protector bug (Nick): https://reviews.llvm.org/D87956 
Arm32 adrl patches get us much closer to assembling arm32 w/ clang
https://github.com/ClangBuiltLinux/linux/issues/430#issuecomment-692904762 
Thanks Jian for fixing https://github.com/ClangBuiltLinux/linux/issues/742 
Saving eflags via builtins is slow 
Missing lore thread :(
https://bugs.llvm.org/show_bug.cgi?id=47530 
https://bugs.llvm.org/show_bug.cgi?id=47531 
pac/bti compiler generated functions may not correctly have the proper fn attr’s. Momchill and Daniel @ ARM are working on this in LLVM.
Open mandriva clang kernels look good in tests. Looking to default to Clang in their next release.
Ppc vdso
@local24pc assembler suffix
LTO patches need help testing
https://lore.kernel.org/lkml/20200918201436.2932360-1-samitolvanen@google.com/ 

## Sep 9, 2020
Plumbers talks + notes: https://github.com/ClangBuiltLinux/plumbers-2020-slides
CrOS boot failure in 4.4
https://bugs.chromium.org/p/chromium/issues/detail?id=1123683
https://bugs.llvm.org/show_bug.cgi?id=47468
Cros stpcpy
https://bugs.chromium.org/p/chromium/issues/detail?id=1125877
https://ozlabs.org/~akpm/mmotm/broken-out/lib-stringc-implement-stpcpy.patch
Android emulator LTO + stack protector failure on 5.4 suspend/resume
https://lore.kernel.org/lkml/20200909184001.GB28786@gate.crashing.org/T/#t
“I've been running it privately now for several months.“
Looks like patch actually using the feature may not have been attached.
LLVM Dev meeting, BoF + talks (sign up now!)
https://llvm.org/devmtg/2020-09/
LTO patches resent (please help test + review)
https://lore.kernel.org/lkml/20200903203053.3411268-1-samitolvanen@google.com/
Trying to fix builtins
https://reviews.llvm.org/D86508
Orphan handling warn in linux-next
TODO: vdso’s need this linker flag, too
“rm”
(No list was cc’ed that provides archives…)
Relaxation patches; pay down the debt
https://github.com/ClangBuiltLinux/continuous-integration/blob/master/patches/llvm-12/5.4/x86_64/0001-x86-boot-compressed-Disable-relocation-relaxation.patch
TODO(Nick): send to stable with more info why it’s necessary and less risky than 6 patch series.
Clang-10 in Ci
Clang-9 might be interesting to test for stable, but we’re not yet testing stable branches with clang.
TODO(Mark): is this useful for nightly llvm builds? https://github.com/ClangBuiltLinux/dockerimage
TODO(Nick): contact Syvestre Ledru about clang 10.1 debian packaging.

## Aug 12, 2020
Plumbers
Tentatively Thursday Aug 27 7am PDT
This is still subject to change
11 talks proposed; likely will cut this down and publish the MC soon.
BoF proposed in addition to MC, both accepted.
i386 now buildable+bootable as of 5.9!
https://github.com/ClangBuiltLinux/linux/issues/194 
-Wa,-mrelax-relocations=no related boot failures on x86_64
https://github.com/ClangBuiltLinux/linux/issues/1121 
Performance wins targeting x86_64
https://reviews.llvm.org/D85257 
https://reviews.llvm.org/D85807 
Clang-tidy / clang-build patches
https://lore.kernel.org/lkml/20200812173958.2307251-1-masahiroy@kernel.org/T/#t 
S390
Issues: https://github.com/ClangBuiltLinux/linux/issues?q=is%3Aopen+is%3Aissue+label%3A%22%5BARCH%5D+s390%22 
CI: https://github.com/ClangBuiltLinux/continuous-integration/issues/232 
Dropped buildroot support: https://github.com/buildroot/buildroot/commit/b24c3215c13b0f25979c744af4b2e58359b5723b 
Initial build in CI: https://github.com/ClangBuiltLinux/continuous-integration/pull/229 
Fixed: https://github.com/ClangBuiltLinux/continuous-integration/issues/152 
Linuxone community cloud: https://developer.ibm.com/components/ibm-linuxone/gettingstarted/ 
Preferred to trying to get a machine for development.
KernelCI has debootstrap images we might be able to use instead of buildroot.
Thanks for guests Ulrich Weigand, Vasily Gorbik, and Ilya Leoshkevich (all from IBM in Germany) for attending and support.

## July 29. 2020
I386 patches in -next
Need folks to chime in/test lld patches
https://www.google.com/url?q=https://lore.kernel.org/lkml/20200717201801.3661843-2-nivedita@alum.mit.edu/T/%23u&sa=D&usg=AFQjCNHkUMej_U5gXbJRktNeaN-UOutzjw 
Plumbers arch talk (may be of interest to discuss which backends need llvm support)
LTO fix for networking
https://lore.kernel.org/lkml/20200708230402.1644819-1-ndesaulniers@google.com/ 
Tracepoint strings fix for /tracing/printk_formats
https://lore.kernel.org/lkml/20200723205341.1099742-2-ndesaulniers@google.com/T/#t 
Save_stack fixes accepted
Another bug in UNWINDER_FRAME_POINTER
https://www.arm.linux.org.uk/developer/patches/viewpatch.php?id=8992/1 
clang-tidy / clang-analyzer v7 GTG
Hint clang-tidy finds a couple bugs in arm arm64 (testers, bugfixers wanted)
https://lore.kernel.org/lkml/20200728004736.3590053-1-nhuck@google.com/ 
Plumbers accepted but not published
Riscv boot failure due to stack protector
https://github.com/ClangBuiltLinux/linux/issues/1092
Clang-11 released
Need to get ci coverage
Known issues with PAC + old binutils
At least 2 new fixes for asm goto backported to clang-11
https://reviews.llvm.org/rG1da9834557cd4302a5183b8228ce063e69f82602
https://reviews.llvm.org/D83708
(tcmalloc developers are making use of asm goto w/ outputs)
LTO merging compoundliterals for kernel modules reverted
Boot failures reported by an Android OEM, haven’t had time to debug.
Replacing compound literals with named global static structs fixes the boot, so there *is* a problem merging them via linker script
https://android-review.googlesource.com/c/kernel/common/+/1361089
Structures with holes and information data leaks from the kernel? (Arnd)
(Kees) See: lib/test_stack_init.c
Orphan section warn
Needs rebasing with asserts for zero size

## July 15, 2020
i386 patches sent to Linus
Plumbers may have an LLVM MC
Asm goto regression needs to get cherry picked to new clang-11 branch
Assembler fixes; Hyperv, x86 crypto. Arm64 regressed
Riscv regressed - still broken though reported upstream? Will check again tomorrow
Add Maxim to Linux Plumbers CI
Kernelci doing boot tests w/ clang-10 linux next
Clang-tidy/static-analyzer patches sent upstream
Orphan section handling uncovering all kinds of bugs
Old binutils causing issues w/ clang-10 and PAC
Apt.llvm.org may going away

## June 17, 2020
Tom Stellar doing github integration for backports for point releases
CrOS issues
R7 thumb (fixed)
https://lore.kernel.org/lkml/20200608205711.109418-1-ndesaulniers@google.com/T/#u 
.text.hot. .text.unlikely. (TODO)
https://chromium-review.googlesource.com/c/chromiumos/third_party/kernel/+/2236871/ 
Integrated as
Ppc32 should be back online after quick LLVM fix
https://github.com/ClangBuiltLinux/linux/issues/1044 
Riscv booting (nhuck)
https://github.com/ClangBuiltLinux/linux/issues/867 
save_stack_trace for arm32 fixed (nhuck)
https://github.com/ClangBuiltLinux/linux/issues/912 
-Wformat is due to narrowing conversions. Too many to fix right now. Lots of easy fixes. (nhuck)
https://github.com/ClangBuiltLinux/linux/issues/378 
Qemu requires -cpu max for pac/bti testing
RELR breaks GDB?
Reworking asm goto, has multiple boot failures
https://reviews.llvm.org/D79794
Quick UBSan fixes on aarch64
https://lore.kernel.org/lkml/20200608203818.189423-1-ndesaulniers@google.com/T/#u 
Nick reviewed a bunch of i386 patches for clang, not sure if they got picked up.
https://lore.kernel.org/lkml/CAKwvOdnj4M6xy3DhqE9U05bBhNEHR7-o8CM0T-KoQFRck0o39g@mail.gmail.com/T/#m1402c54af9c26679397be024244fa6148608742c 
US LLVM dev meeting CFP is up
(Nick) Everything I know about debugging LLVM
(Nick) ClangBuiltLinux BoF
(Bill+Nick) asm goto w/ outputs
https://lists.llvm.org/pipermail/llvm-dev/2020-June/142224.html 
Linaro CFP
Sept 22-24 July 1st CFP deadline
https://sessionize.com/LVC20/ 
unsupported GNU_PROPERTY_TYPE (5) type: 0xc0000000 via aarch64 PAC
https://github.com/ClangBuiltLinux/linux/issues/1054
Kcsan clang-11 only for now
Tons of CFI issues in sysfs
https://github.com/ClangBuiltLinux/linux/issues/1051

## June 3, 2020
Atomisp fixes (Arnd, Nathan)
R7 warnings, compat vdso
Should the compat vdso be configurable?
Clang ia patches (Arnd)
ODR patch from Bob, waiting on x86 folks to pick up
https://lore.kernel.org/lkml/20200515180544.59824-1-inglorion@google.com/T/#mafd13fc1faf858832f30ea09c7ad3678c81ce75b
Huck intro
Focusing on compile time measurement
-fno-eliminate-unused-debug-types (Nick WIP)
https://reviews.llvm.org/D80242
-gz=zlib in kernel
https://lore.kernel.org/lkml/20200526171830.151966-1-ndesaulniers@google.com/ 
32b x86 reviewed
https://lore.kernel.org/lkml/CAKwvOdkB0J8oMjG-NsM6O6BCnodmY8UeYqCyeR-c6NSa5paYfQ@mail.gmail.com/T/#m1402c54af9c26679397be024244fa6148608742c 
Sroa bug
https://bugs.llvm.org/show_bug.cgi?id=40776
Pattern init found a bug in overlayfs
Rust working in the kernel (Nick)
TODO: loadable kernel module support, dynamic allocation, crates
Compat vdso on arm64 hardcodes bfd, doesn’t work right when linked with LLD
https://github.com/ClangBuiltLinux/linux/issues/1033

## May 18, 2020
Cuttlefish ODR violation (Bob): https://lore.kernel.org/lkml/20200515180544.59824-1-inglorion@google.com/T/#u
Compressed debug info (Nick): https://lore.kernel.org/lkml/20200504031340.7103-1-nick.desaulniers@gmail.com/
x86 32b series (Nick reviewing): https://lore.kernel.org/lkml/CAKwvOdmak_L9Rp8FQ+N6-N9vWGH3M-jjP+XJTGUTeYCG9N_dBQ@mail.gmail.com/T/#t 
x86 akpm patch: https://ozlabs.org/~akpm/mmots/broken-out/x86-bitops-fix-build-regression.patch 
ppc qemu: https://groups.google.com/g/clang-built-linux/c/6W3Ee6PByyg/m/bVt-VkJ6AwAJ 
-Wmissing-prototypes (0day bot has enabled W=1)
Kcsan moving to clang-11 only
Builtin memcpy
-Winline-asm r7 waiting on input from gcc but blocking CrOS upgrade
Libabigail -fno-eliminate-unused-debug-types: https://reviews.llvm.org/D80242
Aarch64 assembler issue with expressions being treated as absolut (Jian)

## May 6, 2020
Welcome to Arnd, Randy. (Linaro)
Fortify disabled (Kees, George, Tom)
~2 bugs, primary is that Clang does unusual optimizations around memcpy/strcpy*/…, so this missed some fortify calls in the kernel.
Clang-10 had a bug where it was doing full calls to memcpy() instead of inlining down to smaller sequences. This is fixed, but exposed the first problem.
Fortify is important for compile-time and potentially run-time bounds checking.
GCC is better at issuing diagnostics later during code generation, while Clang struggles with this.
Fix will go in a point release for Clang 10.
https://github.com/ClangBuiltLinux/linux/issues/1002 
Script for filing bugs for Clang releases.
llvm/utils/release/merge-request.sh
More work needs to be done on the kernel side for fortify as well.
X86 LTO 4.19- not booting (Nick)
$local for keeping symbols from being exported.
https://github.com/ClangBuiltLinux/linux/issues/852
X86 -next orb (Nick)
https://lore.kernel.org/lkml/20200505174423.199985-1-ndesaulniers@google.com/T/#u 
32b x86 (Nick)
Close to working, just waiting on one patch to be merged to turn this on.
per cpu and getuser fixes merged.
https://lore.kernel.org/lkml/20200504230309.237398-1-ndesaulniers@google.com/T/#u 
Compressed debug info patch sent (Nick)
Large debug info growth sparked work on this.
Dwarf 5 (need to retest w/ gcc, 5 recent fixes to ToT GNU as)(Nick)
Rust in tree builds working (Nick)
https://lwn.net/Articles/797558/
Plumbers will likely be virtual
Should we just merge with Toolchain MC? (Nick thinks yes)
movzxw mnemonic/pseudo-op not supported by LLVM (Jian, Diab)
Will probably just fix this with an explicit version of the instruction.
Pahole + LTO (Bill)
Networking slowdown (Bill)
Compile bug, missed optimization?
https://groups.google.com/g/clang-built-linux/c/ZCwRi6n_jcw
3 bug requests (Arnd)
Kcov + boundsan or tsan - kcov gets disabled
-Wframe-larger-than can’t be set with a value with a pragma
Can’t print all available warning options - Any ideas on how to get all of this?
https://clang.llvm.org/docs/DiagnosticsReference.html
-Winline-asm warning about any use of r7 in Thumb2
-Wformat (Nick)
https://github.com/ClangBuiltLinux/linux/issues/378#issuecomment-623772712 

## April 22, 2020
Move meeting up one hour? Sounds like this might benefit at least one attendee.
Armv5 boot issue default page alignment
https://bugs.llvm.org/show_bug.cgi?id=45632
X86 stack protector
https://lore.kernel.org/lkml/20200422192113.GG26846@zn.tnic/T/#t 
Asm goto w/ outputs
https://reviews.llvm.org/D78341
https://reviews.llvm.org/D77849
https://reviews.llvm.org/D78166
https://reviews.llvm.org/D78234
https://reviews.llvm.org/D78520
Kernel size regression debug info
Clang-10 ppc and riscv regressions
One outstanding pull Hal has approved for Tom to merge.
Iwmmxt missing support in LLVM, should implement those instructions.
Memcpy fortify
Previous regression fixed
Clang fortify may never have worked for the kernel, Kees and George looking
Zero init cfe-dev thread started by Kees
I spoke with Arnd Bergmann about s390 rootfs images.  He suggested debian deboot strap.  I think we might also be able to cross compile a simple init binary with zig, though I don’t know if s390 support has been well testing in zig.

## April 8, 2020
LLVM=1 patch landing in -next
LLVM_IAS=1 needed for CI
LD is now in /proc/version in -next (Kees).  Android backported to 4.14 and wrote a VTS test for this.
Nick heads down on “asm goto with outputs” bug reports from Linus.
Integrated assembler close
Probably can enable now for x86 for next
arm64 needs CONFIG_KVM .inst parsing fix
arm32 ???
Android had an emergency update to the compiler release clang-r377782d to fix an LLD npd for mainline-x86.  Does CrOS have mainline kernel builds?
Merge window opened for linux 5.7.
ppc nondeterminism issue
0day randconfigs finding lots of issues
KernelCI needs
to upgrade to clang-10
Test more branches
Add more LLVM tools
Need to integrate tuxbuild client into ci
Fortified memcpy issue using ToT LLVM
March 25, 2020
Dtc yylloc patch eye out for stable
Will regress our CI when it lands, as we’re carrying it out of tree for now, but backporting as is won’t be sufficient.
Syzkaller fix
https://lore.kernel.org/lkml/20200323191243.30002-1-ndesaulniers@google.com/
Arm64 ptr auth fix
https://lore.kernel.org/linux-arm-kernel/20200319181951.102662-1-ndesaulniers@google.com/T/#u
Ci changes
KernelCI: https://github.com/kernelci/kernelci-core/pull/340
TODO: enable coverage of mainline and stable now that we have the configs right.
CBL CI: tuxbuild prototyping
Assembler
X86 booting?
Blocked on https://github.com/ClangBuiltLinux/linux/issues/913, works otherwise.
https://github.com/ClangBuiltLinux/linux/issues/669 becomes an error in linux-next, so that needs to be fixed.
Arm64 one llvm bug away for defconfig?
Blocked on https://github.com/ClangBuiltLinux/linux/issues/913, https://github.com/ClangBuiltLinux/linux/issues/939 (potentially more for CONFIG_KVM)
https://github.com/ClangBuiltLinux/linux/issues/716 isn’t a blocker, but is really annoying and should get fixed.
Polly
Aosp llvm: https://android-review.googlesource.com/c/toolchain/llvm_android/+/1261718
Kconfig: https://groups.google.com/g/clang-built-linux/c/ZR7kT_Z0kp4/m/RqwkQ0OkAQAJ 
Linux Plumbers Conf micro conf proposals just opened, plan to do a ClangBuiltLinux micro conference.
https://www.linuxplumbersconf.org/blog/2020/
Request for test: https://lore.kernel.org/lkml/20200317215515.226917-1-ndesaulniers@google.com/T/#u

## March 11, 2020
Issues with -fno-common flag. Nathan discovered it has to deal with the device tree compiler (dtc).
Might be an issue with it being built by the host compiler, and it might be broken for TOT gcc as well.
PowerPC patch from Christopher Leroy.
Broken compile-time assert for Intel (from last week).
Issue with const struct designated initializers.
Nick has an idea of how to fix this.
Parsing asm inline better - https://reviews.llvm.org/D75563
Nathan submitted his first patch to Clang - https://reviews.llvm.org/D75758. Congrats! :)
491 patches for converting fallthrough comments on the kernel.
Richard Smith ripped out comment parsing from Clang.
https://reviews.llvm.org/D73852#1901694
Symbol visibility issue for lib-y vs obj-y. Sparc had an issue (Masahiro fixed) Last issue for x86 allmodconfig.
Now has hit an issue in MIPS.
RISC-V support needed in our CI.
0-day bot and kernelci are both building configs with Clang.
Out of tree patches for the CI for -fno-common We do this sometimes to fix really bad situations.
2 operand assembly issue where 2 of them are zero, but can be solved a few different ways.
Tuxbuild microservice from Linaro
Might convert some of our TravisCI.
YAML
Local builds

## February 26, 2020
Bolt vs. Propeller post-LTO
Kees’ linker warning cleanup (less than 100 lines changed)
ChromeOS using LLD + Clang everywhere now
4.4 vdso still using bfd due to some missing patch related to a linker script name.
ChromeOS kernels 4.14 and 4.19 are now using pattern initialization.
One issue still causing crashes.
ARM suggests Oliver Stannard as a code reviewer in preference to Peter Smith for issues, especially with integrated assembler bugs.
Red Hat meeting
4000+ packages that they want to use as a continuous integration test for LLVM.
Curious about userspace switch to Clang/LLVM.
Ubuntu director of kernel engineering
Adding a Clang built source package would be pretty easy apparently.
Portland trip might allow in-person conversations with Canonical and Linus.
Linus + asm goto with output constraints
Built a Clang with Bill’s patch for output constraints.
Used that to build Linux with his patches using it.
Responded with a few bugs that were fixed within hours of reporting them.
Positive feedback about Clang codegen.
Perf showing 2 GCC instances in comment block of executable via objdump
One comes from working with glibc.
Other one is probably a non-hermetic build issue.
Congrats to Bill for asm goto with outputs landing on Monday
Register live-in info is unexpected until after register allocation.
Terminator form of copy instruction.
Phi node choosiness.
-Werror for prod kernel builds
Primarily in KVM unit tests.
Bill sent out a lot of patches for review.
First Clang-built prod kernel will be 903. 900 is current one they are working on. So maybe April. :)
kselftests seem to all be built with explicit GCC
Plea from Nick to remember to CC mailing list on any upstream patches
Fangrui mentions being interested in fixing integrated assembler issues, so that he can remove gas.
Reserved register r7 warning cleanup
Maybe this shouldn’t be emitted if we are using -fomit-frame-pointer.
Zero day bot builds with Clang are live!
Emails being sent when they break.
One x86 maintainer acknowledged fixing a break (probably without knowing it was a Clang issue).
KernelCI
Documentation patch for building kernel with Clang sent for review
Maybe a warning for version < Clang-9 use.
