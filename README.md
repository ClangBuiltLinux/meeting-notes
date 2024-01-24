# Clang-Built Linux Meeting Notes

Notes from our meeting every other week. See
[our homepage](https://clangbuiltlinux.github.io/) for links to the calendar
invite and meet link.

Send to: llvm@lists.linux.dev

## Jan 24, 2024
- (Nathan) UML breakage with `clang-18`
  - [Issue 1](https://github.com/ClangBuiltLinux/linux/issues/1981), [Issue 2](https://github.com/ClangBuiltLinux/linux/issues/1982)
  - [Fixes](https://lore.kernel.org/20240123-fix-uml-clang-18-v1-0-efc095519cf9@kernel.org/)
- [s390 `ld.lld` support](https://github.com/llvm/llvm-project/pull/75643)
- (Nathan, Justin) Tree updates in continuous-integration ([drop 4.14](https://github.com/ClangBuiltLinux/continuous-integration2/commit/6fbc9a2ef8950499a1496d08b5b2e23b11666ead), [add new ChromeOS branches](https://github.com/ClangBuiltLinux/continuous-integration2/commit/5a71921bc040a2c5d1bfcb1e47efbfcf853ec87e))
- [RISC-V LTO accepted](https://git.kernel.org/riscv/c/021d23428bdbae032294e8f4a29cb53cb50ae71c)
- LLVM tip of tree is now 19, `release/18.x` branched
  - [Announcement](https://discourse.llvm.org/t/release-18-x-branch-has-been-created/76480)
  - [Release schedule](https://discourse.llvm.org/t/llvm-18-release-schedule/76175)
  - [CI game plan](https://github.com/ClangBuiltLinux/continuous-integration2/issues/686)

## Jan 10, 2024
- (Fangrui) RISC-V LLVM main boot regression ([issue](https://github.com/ClangBuiltLinux/linux/issues/1965), [fix](https://github.com/llvm/llvm-project/commit/6c207ee5d20d2b054509123e6d0507df1332b376))
- (Justin) [Continuous integration caching](https://github.com/ClangBuiltLinux/continuous-integration2/pull/664)
- (Nathan) RFC for bumping minimum supported version to 13.0.1 ([mailing list](https://lore.kernel.org/20240110165339.GA3105@dev-arch.thelio-3990X/), [GitHub](https://github.com/ClangBuiltLinux/linux/issues/1975))
- LoongArch can now build without any disabled configurations with LLVM main because [`__attribute__((model("extreme")))` is now supported in `clang`](https://github.com/llvm/llvm-project/commit/4df566290751403f470fea3b27aa148ab1ddf144)
- [New fortify warning in `fs/smb/client/cifsencrypt.c`](https://github.com/ClangBuiltLinux/linux/issues/1966)
- [New instance of `-Wenum-enum-conversion` in `# drivers/gpu/drm/amd/display/dc/link/protocols/link_dp_dpia_bw.c`](https://github.com/ClangBuiltLinux/linux/issues/1976) in -next ([fix](https://lore.kernel.org/20240110-amdgpu-display-enum-enum-conversion-v1-1-953ae94fe15e@kernel.org/))
- `release/18.x` is scheduled to be created in two weeks, get changes landed ASAP targetting `clang-18`

## Nov 29, 2023
- [RISC-V linker failure around `R_RISCV_{SET,SUB}_ULEB128`](https://github.com/ClangBuiltLinux/linux/issues/1961)
- [LoongArch `CONFIG_RELOCATABLE` fix](https://lore.kernel.org/20231124035534.70432-1-wangrui@loongson.cn/)
- (Nathan) `__muloti4` generation issue
  - [Issue](https://github.com/ClangBuiltLinux/linux/issues/1958)
  - [Workaround patch](https://lore.kernel.org/20231128-avoid-muloti4-grow_buffers-v1-1-bc3d0f0ec483@kernel.org/)
- (Nathan) LLVM 17.0.6 released and [uploaded to kernel.org](https://lore.kernel.org/20231128194910.GA3062541@dev-arch.thelio-3990X/) (last 17.x release for the time being)
- (Justin) Continuous integration v3
- (Nick) Work on `rm` constraints
- (Bill) Work on `__counted_by`
- [Plumbers videos live](https://www.youtube.com/playlist?list=PLVsQ_xZBEyN0rGt1cmVhPn_TG79YfS_gX)

## Nov 1, 2023
- (Maxim) [Protecting Compiler Optimizations with Linaro Benchmarking CI](https://www.youtube.com/live/ydAOVJqeL5o?si=sO7gCJb9vxJ1LwLh)
- bcachefs -Wframe-larger-than 32b arm [report from linaro](https://lore.kernel.org/llvm/1310397379.52558.1698849730427@jenkins.jenkins/)
- (Nathan) -Wsometimes-uninitialized in bcachefs
- (Nathan) -Wc23-extensions [in mainline](https://github.com/ClangBuiltLinux/linux/issues/1953) due to ~3 days in -next
- (Nathan) [loongarch breakage](https://github.com/ClangBuiltLinux/linux/issues/1955)
- (Bill) `__attribute__((counted_by()))` has landed, Bill working on fixups
  - GCC folks mentioned potential data dependency issues
- (Mark) LTO and ARM64 discussion on IRC about the use of ALTERNATIVES in READ_ONCE
  - acceptable to remove upgrading to rcpc when available?
- Has the Itanium sunk?
- (Nick) distracted with "rm"
- (Tom) llvm-17 release
- (Nathan) 17.0.4 binaries on kernel.org

## Oct 18, 2023
- [arm64 boot failure](https://github.com/ClangBuiltLinux/linux/issues/1946)
  - looking like a compiler bug
- bug scrub last week
- llvm dev conf last week
  - discussions around stack usage, `-fbounds-safety`
- [riscv LTO](https://github.com/ClangBuiltLinux/linux/issues/1942) has an issue with LLD not respecting relaxation
- header refactoring
  - circular includes
- (Nick) inline asm "rm" work

## Jul 26, 2023
- [asm goto error diagnostic fixed](https://github.com/ClangBuiltLinux/linux/issues/1886)
- [improving constant expression evaluation](https://github.com/ClangBuiltLinux/linux/issues/1889)
- [perf LTO](https://lore.kernel.org/llvm/20230724201247.748146-1-irogers@google.com/)
- LoongArch LLD support landed in clang-17
  - [tuxmake work](https://github.com/ClangBuiltLinux/continuous-integration2/issues/599) for CI; hexagon prior-art?
- [qemu x86 tcg issue](https://github.com/ClangBuiltLinux/boot-utils/issues/111)
- [powerpc missing instruction](https://github.com/ClangBuiltLinux/linux/issues/1891)
- Discussion around promoting W=1 warnings to always on, even if some architectures have lingering instances
- release/17.x branched
  - [update CI](https://github.com/ClangBuiltLinux/continuous-integration2/issues/608)
- [`-fbounds-safety` video published](https://youtu.be/RK9bfrsMdAM)
- [KASAN + LTO fixes](https://github.com/ClangBuiltLinux/linux/issues/1721)
- [indirect/computed goto error diag](https://github.com/ClangBuiltLinux/linux/issues/1890)
- [reduce scripts](https://github.com/ClangBuiltLinux/reduce/pull/1)

## Jul 12, 2023
- `--gc-sections` [for RISCV](https://github.com/ClangBuiltLinux/linux/issues/1881)
  - no update 
- Loongarch [support for LLD is close](https://reviews.llvm.org/D138135) and necessary to start kernel builds with LLVM=1
- `-fstrict-flex-arrays=3` triggering `-Warray-bounds` in SCSI code in [mainline](https://github.com/ClangBuiltLinux/linux/issues/1851)
  - Arnd's [fix accepted](https://git.kernel.org/pub/scm/linux/kernel/git/jejb/scsi.git/commit/?id=47699a2b63caaa0de4841d4402627c2fdf3452a6)
  - James Bottomley confirms in private email thread that PR will be sent Friday-ish
- (Nathan) PPC64 (BE) now building with [LLVM=1](https://github.com/ClangBuiltLinux/continuous-integration2/pull/593)
- (Sami) [kCFI for RISCV](https://lore.kernel.org/lkml/20230710183544.999540-8-samitolvanen@google.com/)
- (Space) working on moving syzbot builds to LLVM=1
- (Yonghong) [fix](https://lore.kernel.org/lkml/20230628181926.4102448-1-yhs@fb.com/) for livepatch + LTO
- [EuroLLVM videos being posted](https://www.youtube.com/playlist?list=PL_R5A0lGi1AD-bqRaY61l5Q-EozbfyLZr)
  - [2023 EuroLLVM - Optimizing the Linux Kernel with LLVM BOLT](https://youtu.be/ivTCCTSMGZg)

## Jun 28, 2023

- [CFP for Toolchains Track at Linux Plumbers 2023](https://lore.kernel.org/llvm/CAKwvOdk6VP4ejRJk_+Q_Smj_=Ly0dd8nyAiXJb+w18y6VJb7YQ@mail.gmail.com/)
- [ClangBuiltLinux meetup 2023](https://clangbuiltlinux.github.io/meetup.html)
- [RISC-V ld.lld dead code elimination performance regression](https://github.com/ClangBuiltLinux/linux/issues/1881)
- [Continued fallout from `clang` changing certain options to be target specific](https://github.com/ClangBuiltLinux/linux/issues/1878)
- s390 link error in decompressor ([issue](https://github.com/ClangBuiltLinux/linux/issues/1747), [patch](https://lore.kernel.org/20230622125508.1068457-1-hca@linux.ibm.com/))
- LoongArch building with certain configurations disabled as of `next-20230628`
  - [tracking issue](https://github.com/ClangBuiltLinux/linux/issues/1787)
  - [initial Linux support](https://lore.kernel.org/20230625095644.3156349-1-kernel@xen0n.name/)
  - [cross compile fixes](https://lore.kernel.org/20230627130122.1491765-1-kernel@xen0n.name/)
  - [boot-utils support](https://github.com/ClangBuiltLinux/boot-utils/pull/109)
- Further discussion around [Apple's `-fbounds-safety` LLVM proposal](https://discourse.llvm.org/t/rfc-enforcing-bounds-safety-in-c-fbounds-safety/70854/72)
  - Proposed competing `__element_count__` attribute [merged for 6.5-rc1](https://git.kernel.org/linus/dd06e72e68bcb4070ef211be100d2896e236c8fb)

## Jun 14, 2023
- [Group diagnostics & specificity differences](https://github.com/llvm/llvm-project/issues/63315)
- (Nathan) "kbuild: Update assembler calls to use proper flags and language target" [backports](https://lore.kernel.org/stable/20230612-6-1-asssembler-target-llvm-17-v1-0-75605d553401@kernel.org/)
- (Nathan) `-Wunused-variable` and `__attribute__((cleanup()))` [fix](https://reviews.llvm.org/D152180)
- (Nathan) [boot-utils images moved to GH releases](https://github.com/ClangBuiltLinux/continuous-integration2/pull/577)
- [ftrace disabled for 32b ppc](https://lore.kernel.org/llvm/20230609034501.407971-1-naveen@kernel.org/)
- riscv MEDLOW
  - disable for COMPILE_TEST?
    - CONFIG_ARM_MODULE_PLTS might do something similar
- [s390 series](https://git.kernel.org/pub/scm/linux/kernel/git/niks/linux.git/log/?h=has_ioport_v5)
- [ppc allmod stack frame - due to sanitizers?](https://lore.kernel.org/all/202306131418.35B5D649DC@keescook/)
- (Arnd) [lots of W=1 warning fixes](https://pastebin.com/yGRqEE8p)

## May 31, 2023
- (Anders) QEMU 7.2 regression?
  - https://lore.kernel.org/lkml/f0194cbe-eb5b-40ee-8723-1927ebddefc1@app.fastmail.com/
- `-Wstrict-flex-arrays=3`
  - https://github.com/ClangBuiltLinux/linux/issues/1858
  - https://github.com/ClangBuiltLinux/linux/issues/1851
- `-Wbuiltin-macro-redefined`
  - https://github.com/ClangBuiltLinux/linux/issues/1855
  - https://reviews.llvm.org/D151741
- arm64be vdso https://github.com/ClangBuiltLinux/linux/issues/1859
- stack protector issue https://github.com/ClangBuiltLinux/linux/issues/1854
- (Nathan) rewrite boot-utils to DL initrd images
- LLVM meetup planning before plumbers
- [US LLVM dev conf announced](https://discourse.llvm.org/t/save-the-date-for-the-2023-us-llvm-developers-meeting/70848) 


## May 17, 2023
- (Yonghong, Song) LTO
  - improvements in perf (ThinLTO only tested so far) webserver 0.3%
  - Live patch
    - issue with strings being promoted to globals, non-deterministic hash value
    - Let's meet with Pete Swain
- (Maksim) BOLT
  - post-link optimizations
  - good perf gains over LTO+PGO depends on the workload though
  - kernel is booting in vm and now on hardware
  - interesting perf workloads?
  - not full optimizations enabled yet (safety) maybe only ~50%
  - how is perf collected?
  - test cases?
  - a few unlikely/likely are wrong
- Boot failures
  - [android ARCH=arm](https://github.com/ClangBuiltLinux/linux/issues/1848)
  - [next ARCH=i386](https://lore.kernel.org/linux-next/CA+G9fYvhPgoP57ip1cW5TaWJfkbkHA2SZqd5fFoTJ7rDGA138w@mail.gmail.com/)
- PIE issues x86
  - [No debug info for stack guard checks](https://github.com/llvm/llvm-project/issues/62480)
  - x86 stack protector code references `@GOTPCREL` and `@PLT` even when built with `-fno-pic` or `-fno-pie`.
    - https://github.com/llvm/llvm-project/issues/62481 
    - https://github.com/llvm/llvm-project/issues/60116 
  - [inefficient segment register relative access](https://github.com/llvm/llvm-project/issues/62482)
  - [Inline asm P output template](https://github.com/llvm/llvm-project/issues/60096)
- (Arnd) 140 patches sent for fixing missing prototypes
- (Fangrui) SFrame


## May 3, 2023
- (Fangrui) [arm64 linker script fixup](https://lore.kernel.org/linux-arm-kernel/20230502074105.1541926-1-maskray@google.com/)
- (Nathan) [PPC allmodconfig building!](https://github.com/ClangBuiltLinux/continuous-integration2/pull/562)
- (Nick) [android-4.19 boot failure fix](https://reviews.llvm.org/D149191)
- (Yonghong) [pahole fix for DW_ATE_unsigned_1024](https://lore.kernel.org/dwarves/20230426055030.3743074-1-yhs@fb.com/)
- (Bill) [element_count prototype](https://reviews.llvm.org/D148381)
- (Bill) [CBL meetup](https://lore.kernel.org/llvm/CAGG=3QXHK2XhBBV0XwUok-Cop_+xJZtB_D1=qMS6HwWoKs8Hag@mail.gmail.com/) Nov 11 Saturday before Plumbers
- x86 pie patches mention some issue with clang
- [KASAN stack option discussion](https://lore.kernel.org/all/96947fdc-835f-4bfa-b112-4ba9991cfe5f@app.fastmail.com/)
- (Arnd) missing prototype W=1 fixes
  - [adobe/orc for validating debug info](https://github.com/adobe/orc)
- [Sframe](https://lore.kernel.org/linux-toolchains/20230501200410.3973453-1-indu.bhagat@oracle.com/)
  - will clang support be necessary?
- [riscv assembler .option directive](https://reviews.llvm.org/D123515)

## Apr 19, 2023
- llvm 16.0.2 [released](https://github.com/llvm/llvm-project/releases/tag/llvmorg-16.0.2)
  - Nathan [posted](https://lore.kernel.org/20230419180635.GA1965688@dev-arch.thelio-3990X/) builds to kernel.org
- llvm [regression](https://github.com/ClangBuiltLinux/linux/issues/1833) related to shrink-wrapping backed out.
- (Nick) Dealing with [fallout](https://github.com/ClangBuiltLinux/linux/issues/1815) from CHOP attack paper
  - [add](https://lore.kernel.org/llvm/20230412-no_stackp-v2-0-116f9fe4bbe7@google.com/) no_stack_protector fn attr to kernel
- (Nick) [improving](https://reviews.llvm.org/D141451) diagnostics for FORTIFY
- (Jiaxun) MIPS [improvements](https://lore.kernel.org/llvm/20230414080701.15503-1-jiaxun.yang@flygoat.com/)
- (Sami) [kCFI for RISCV](https://reviews.llvm.org/D148385)
- (Fangrui) [update linker flags for RELR](https://lore.kernel.org/linux-kbuild/20230411200944.2591330-1-maskray@google.com/)
- [clangd discussion](https://lore.kernel.org/llvm/20230414005309.GA2198310@google.com/)
- plumbers planning starting
  - Toolchain MC again, start thinking about ideas
  - Nov 13-15 (Mon-Wed)
  - Richmond, VA (Venue announced)
  - clangbuiltlinux will be adjacent (maybe before, maybe)
- __builtin_object_size changes planned for GCC, need similar changes for clang
- (Arnd) build fails cross compiling 32b x86 targets for arm64 hosts in the samples/ directory
  - Maybe a patch to test reverting
- (Maxim) reworking notification of kernel+llvm testing

## Apr 5, 2023

- Tom working on cleaning up unused inline functions and unused but set variables ([archive](https://lore.kernel.org/llvm/?q=d%3A2023-03-22..2023-04-05+f%3Atrix%40redhat.com))
- Nick continuing to investigate [LTO boot issue on android-4.14-stable](https://github.com/ClangBuiltLinux/linux/issues/1815)
- [`ARCH=powerpc allmodconfig` in continuous-integration](https://github.com/ClangBuiltLinux/continuous-integration2/pull/536) (Nathan)
- Stable versions of LLVM now on [kernel.org](https://mirrors.edge.kernel.org/pub/tools/llvm/) (Nathan)
- MIPS positional parameter warning [fix](https://lore.kernel.org/20230404-mips-unused-named-parameters-v1-1-71d6c656f1de@kernel.org/) (Nathan)
- [Adjust dependencies for dynamic ftrace for RISC-V ](https://lore.kernel.org/20230404-riscv-dynamic-ftrace-checks-clang-v1-1-0ce296b7d423@kernel.org/)(Nathan)
- [5.10 backports](https://lore.kernel.org/20230328-riscv-zifencei-zicsr-5-10-v1-0-bccb3e16dc46@kernel.org/) for RISC-V `zifencei` and `zicsr` (Nathan)
  - It appears LLVM has [no intention of matching binutils behavior around `zifencei` and `zicsr`](https://reviews.llvm.org/D147179).
- [kexec regression with LLVM 16+](https://lore.kernel.org/20230321-kexec_clang16-v5-0-5563bf7c4173@chromium.org/) (mailing list not CC'd, found by browsing lore)
- Masahiro looking to [remove `CROSS_COMPILE` determining `--target`](https://lore.kernel.org/20230401170117.1580840-1-masahiroy@kernel.org/)
- RISC-V enabling ACPI, exposing old issue in Hisilicon crypto driver ([patch](https://lore.kernel.org/20230404182037.863533-24-sunilvl@ventanamicro.com/), [bug](https://github.com/ClangBuiltLinux/linux/issues/999))
- Arnd looking into fixing `-Wmissing-prototypes` for ARM and x86

## Mar 22, 2023
- (Nathan) PPC64 (BE) + LLD support
  - additional issue related to CROSS_COMPILE being set to 32b target?
- (Nathan) [boot-qemu](https://github.com/ClangBuiltLinux/boot-utils/pull/91) and [tc-build](https://github.com/ClangBuiltLinux/tc-build/pull/226) rewrites
- (Nick) [improving backend diagnostics](https://discourse.llvm.org/t/rfc-improving-clangs-middle-and-back-end-diagnostics/69261)
- (Nick) [`-Wfunction-fallthrough`](https://reviews.llvm.org/D146466)
- (Bill) [s390 fortify issue](https://github.com/ClangBuiltLinux/linux/issues/1781)
- [clang-16 officially released](https://discourse.llvm.org/t/llvm-16-0-0-release/69326)
  - [android-4.14 boot regression](https://github.com/ClangBuiltLinux/linux/issues/1815)
- (Nick) backend term issue https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=efbcbb12ee99f750c9f25c873b55ad774871de2a
- Linus [asked](https://lore.kernel.org/all/CAHk-=whdrvCkSWh=BRrwZwNo3=yLBXXM88NGx8VEpP1VTgmkyQ@mail.gmail.com/) about maybe eliminating ARCH and CC and adding those to kconfg
- (Kees) [call used regs paravirt case has come up again, now with GCC](https://git.kernel.org/pub/scm/linux/kernel/git/tip/tip.git/commit/?h=x86/paravirt&id=11af36cb898123fd4e0034f1bc6550aedcc87800)
- (Nathan/Connor) [mixed toolchain riscv issue](https://github.com/ClangBuiltLinux/linux/issues/1808)
- (Marco) [remove -g for kfence tests](https://github.com/ClangBuiltLinux/linux/issues/1816)

## Mar 8, 2023
- (Nick) scaling down CI
- (Nick/Bill) ["p" constraint](https://lore.kernel.org/lkml/20230303231133.1486085-1-eranian@google.com/)
- (Conor) [riscv breakages due to extensions moving out of I spec](https://github.com/ClangBuiltLinux/linux/issues/1808)
- [ICC support is gone](https://www.phoronix.com/news/Linux-6.3-Drops-Intel-ICC)
- (Nathan) [ppc mtune flags](https://reviews.llvm.org/D144967)
- ppc64 (BE) elfv2 testing possible now
- [MIPS issue w/ `beqcz`](https://lore.kernel.org/llvm/20230225214500.7446-1-jiaxun.yang@flygoat.com/)
- s390 and hexagon ioport support optional allmodconfig null ptr deref series being rebased

## Feb 22, 2023
- (Nick) [asm goto with outputs on indirect edges](https://github.com/llvm/llvm-project/issues/53562) landed in clang-17
  - One bug report so far: https://github.com/llvm/llvm-project/issues/60855
- (Nick) [KASAN + `CONFIG_FORTIFY_SOURCE=y` fix](https://reviews.llvm.org/D144057)
- (Nathan) [`clang-16` in continuous integration](https://github.com/ClangBuiltLinux/continuous-integration2/pull/516)
- (Nathan) [`CONFIG_PPC64_BIG_ENDIAN_ELF_ABI_V2` series](https://lore.kernel.org/20230118-ppc64-elfv2-llvm-v1-0-b9e2ec9da11d@kernel.org/)
- [clang conditional tail call static call fixes](https://github.com/ClangBuiltLinux/linux/issues/1774) merged
  - (Nathan) [backports for stable](https://lore.kernel.org/Y%2FUf9WUi%2FrANmOk8@dev-arch.thelio-3990X/)
- RISC-V ISA extensions causing interop issues with binutils
  - (Connor) [Recent issue reported on 5.10](https://github.com/ClangBuiltLinux/linux/issues/1808) (likely needs Linux fix)
  - [Older issue](https://github.com/ClangBuiltLinux/linux/issues/1777) (getting fixed in LLVM/`ld.lld`)
- [PowerPC `-mtune` issue](https://github.com/ClangBuiltLinux/linux/issues/1799)
- (Nathan) Python utility updates using classes for better organization and flow, testing appreciated!
  - [boot-utils](https://github.com/ClangBuiltLinux/boot-utils/pull/91)
  - [tc-build](https://github.com/ClangBuiltLinux/tc-build/pull/226)
- [Revisting caching in continuous integration](https://github.com/ClangBuiltLinux/continuous-integration2/issues/308#issuecomment-1440832707)

## Feb 8, 2023
- (Bill) [randstruct fix](https://reviews.llvm.org/D143300) - [report](https://lore.kernel.org/llvm/20230208065133.220589-1-ebiggers@kernel.org/)
- FOSDEM (2 clang built kernels)
  - [Chimera Linux](https://www.phoronix.com/news/BSD-LLVM-Linux-Alpha-Coming) - 22:00 timestamp
  - [Fedora Asahi](https://www.phoronix.com/news/Fedora-Asahi-Remix-2023) - 13:13 timestamp
- [fortify issue](https://github.com/ClangBuiltLinux/linux/issues/1687)
- [boot failure report](https://github.com/ClangBuiltLinux/linux/issues/1800)
- (Serge)[auto-init optimization](https://reviews.llvm.org/D137707)
- [objtool memory reduction patch set](https://github.com/ClangBuiltLinux/linux/issues/1768#issuecomment-1423074854)

## Jan 25, 2023
- (Nick)
  - yet another issue with `-fzero-call-used-regs`: https://reviews.llvm.org/D138757
  - get [more aggressive](https://reviews.llvm.org/D111456) about inlining functions containing `__builtin_constant_p`
    - CrOS' toolchain wrapper is setting `-fdebug-info-for-profiling`, which changes the behavior of inlining in non-obvious ways
  - [blog post](https://nickdesaulniers.github.io/blog/2023/01/20/debugging-wframe-larger-than/) on debugging `-Wframe-larger-than=`
    - converted by blog to hugo
  - [Discussion](https://github.com/ClangBuiltLinux/linux/issues/1793) with HJL (GCC) about asm goto and endbr
- (Nathan)
  - [fix](https://android-review.git.corp.google.com/c/kernel/common/+/2395938) `-Wsingle-bit-bitfield-constant-conversion` is downstream Android Fuse driver
  - [armv4 lld](https://github.com/ClangBuiltLinux/linux/issues/964#issuecomment-1387639749)
- (Kees)
  - blog post [Bounded Flexible Arrays in C](https://people.kernel.org/kees/bounded-flexible-arrays-in-c)
  - [KSPP meeting now public](https://fosstodon.org/@kees/109745781202896756) - [see also](https://lore.kernel.org/linux-hardening/202301241110.DE9769A8@keescook)
- LWN [article](https://lwn.net/Articles/919570/) about 4.9.y EOL
- [Who's hiring](https://discourse.llvm.org/t/ask-llvm-whos-hiring-jan-23/67894)
- clang-16 branched
  - file todo about CI
- (Arnd) [DebVM](https://salsa.debian.org/helmutg/debvm/)

## Jan 11, 2023
- (Nathan)
  - [remove](https://lore.kernel.org/llvm/20221228-drop-qunused-arguments-v1-0-658cbc8fc592@kernel.org/) `-Qunused-arguments`
  - [2022 ClangBuiltLinux Retrospective](https://nathanchance.dev/posts/2022-cbl-retrospective/)
- (Sami) kCFI fixes
  - [Set patchable-function-prefix for synthesized functions](https://reviews.llvm.org/D141172)
  - [Set !kcfi_type metadata for indirectly called functions](https://reviews.llvm.org/D141444)
- 15.0.7 release for `-fzero-call-used-regs` issue
- (Nick)
  - [asm goto w/ outputs along indirect edges](https://discourse.llvm.org/t/rfc-syncing-asm-goto-with-outputs-with-gcc/65453/8?u=nickdesaulniers)
  - [report inlining decisions with -Wattribute-{warning|error}](https://reviews.llvm.org/D141451)
  - profiling WG
- (Bill) validating profile data from sampling
- (Arnd)
  - LKFT regressions reported
  - [link not converging](https://lore.kernel.org/lkml/?q=error%3A+assignment+to+symbol+__init_end+does+not+converge) [repro](https://drive.google.com/file/d/1hqFiEY8rUesFH4pujeEyA1RH5uAZxI95/view?usp=sharing)
- stable 4.9.y is EOL

## Dec 14, 2022
- (Lee) AMDGPU driver disabled for non-32b targets
  - https://github.com/llvm/llvm-project/issues/41896
  - https://lore.kernel.org/llvm/20221125120750.3537134-2-lee@kernel.org/
- [ppc boot failure](https://github.com/ClangBuiltLinux/linux/issues/1770)
- [zero call used regs](https://github.com/ClangBuiltLinux/linux/issues/1766#issuecomment-1352013261) [llvm patch](https://reviews.llvm.org/D139679)
- difficulties w/ randconfig testing due to CONFIG_DEBUG_INFO increasing build times
  - perhaps we need a dedicated KCONFIG option for ALLYESCONFIG/ALLMODCONFIG or RANDCONFIG
- kCFI
  - [Rust interop](https://reviews.llvm.org/D139395)
  - (sami) [kCFI seal](https://reviews.llvm.org/D138337)
  - (Joao) [ibt-seal disabling w/ thinLTO](https://reviews.llvm.org/D140035)

## Nov 30, 2022

- (Nathan) [Fix for `__thumb2__` warnings accepted](http://git.armlinux.org.uk/cgit/linux-arm.git/commit/?id=59e2cf8d21e05391c42628eb9fb5bb40f9d9698f)
- (Nathan) [Fix for lack of modpost warnings with LTO](https://lore.kernel.org/20221129190123.872394-1-nathan@kernel.org/)
- (Nathan) Investigating [-tip `objtool` memory usage regression](https://gitlab.com/Linaro/tuxsuite/-/issues/183)
- (Kees + Bill) `SIGPIPE` handler revert merged into LLVM main and released in 15.0.6
  - https://github.com/ClangBuiltLinux/linux/issues/1651
  - https://github.com/llvm/llvm-project/issues/59037
  - https://github.com/llvm/llvm-project/commit/4787efa38066adb51e2c049499d25b3610c0877b
- [`objtool` build system improvements](https://lore.kernel.org/20221122001125.765003-1-irogers@google.com/)
- [`ARCH=arm allmodconfig -Werror`](https://lore.kernel.org/20221125120750.3537134-1-lee@kernel.org/)

## Nov 2, 2022

- (Sami) [`-Wincompatible-function-pointer-types-strict`](https://github.com/ClangBuiltLinux/linux/issues/1745)
- (Nathan) [Fixes for `-Wincompatible-function-pointer-types-strict`](https://github.com/ClangBuiltLinux/linux/issues/1750)
- (Nick) [support for `-gz=zstd`](https://lore.kernel.org/20221020175655.1660864-1-ndesaulniers@google.com/)
- (Nick) [asm goto with outputs along indirect edges](https://reviews.llvm.org/D136497), which found [a GCC bug](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=107385)
- (Bill) [`-fstrict-flex-arrays=3` landed](https://github.com/llvm/llvm-project/commit/7f93ae808634e33e4dc9bce753c909aa5f9a6eb4)
- (Joao) [emitting `0xcc` for `-fpatchable-function-entry`](https://lore.kernel.org/1f6069657f4630c36d60baab2e9b3d10@overdrivepizza.com/)
- [arm64 AMDGPU `-Wframe-larger-than`](https://github.com/ClangBuiltLinux/linux/issues/1752)
- LoongArch asm fixes, might be able to compile Linux soon?
  - [`[Clang][LoongArch] Support inline asm constraint 'J'`](https://github.com/llvm/llvm-project/commit/cd0174aacb734904205ed7827fb923acda08f79a)
  - [`[LoongArch] Support inline asm operand modifier 'z'`](https://github.com/llvm/llvm-project/commit/e415cb1d61e798b6d69b5960a90f00518ca5008f)
- [FineIBT queued in `x86/core`](https://git.kernel.org/pub/scm/linux/kernel/git/tip/tip.git/log/?h=0c3e806ec0f9771fa1f34c60499097d9260a8bb7)
- [s390 misaligned symbol linker errors](https://github.com/ClangBuiltLinux/linux/issues/1747)
- [s390 requiring clang 15.0.0](https://lore.kernel.org/20221031123456.3872220-1-hca@linux.ibm.com/)
- [New instance of recordmcount issue](https://github.com/ClangBuiltLinux/linux/issues/981#issuecomment-1290981312)
- [Initial glibc clang patches submitted](https://sourceware.org/pipermail/libc-alpha/2022-October/143036.html), [slimmed down v2](https://sourceware.org/pipermail/libc-alpha/2022-November/143148.html)

## Oct 19, 2022
- (Nick) asm goto w/ outputs along indirect edges
- (Nick) backporting debug info for dwarf
  - watch for conflicts w/ Nathan's backports for riscv debug info.
- (Paul) [working on more info](https://reviews.llvm.org/D135488) when `-Wframe-larger-than=` are encountered
- Discussions with tuxsuite/Linaro on [docker containers](https://gitlab.com/Linaro/tuxsuite/-/issues/84)
- kernel.org clang binaries
  - helpdesk kernel.org ticket
- [ICC support removed from kbuild](https://www.phoronix.com/news/Linux-Kernel-Drop-ICC)
- (Bill) PGO new format, compiler-ABI implications
- (Bill) AutoFDO testing/WIP
- (Bill) [`-fstrict-flex-arrays=3`](https://reviews.llvm.org/D134902)
- kCFI
  - [ASAN](https://github.com/ClangBuiltLinux/linux/issues/1742)
  - [ftrace](https://github.com/ClangBuiltLinux/linux/issues/1743)
  - FineIBT patchset inbound (new version in the works)
  - constant blinding bpf
- x86 PKS (kernel changes)
- glibc w/ clang skunkworks
  - Let's talk w/ Bero about https://github.com/OpenMandrivaAssociation/glibc
- (Craig) improving division by constant
  - Clang will be missing support for signed divisions

## Oct 5, 2022
- (Nick) Android toolchain upgrades
  - i386
    - [memmove LTO issue](https://lore.kernel.org/llvm/20221018172155.287409-1-ndesaulniers@google.com/)
    - [stack useage](https://lore.kernel.org/llvm/20221011205547.14553-1-ndesaulniers@google.com/)
  - arm
    - [uldivmod in nwfp](https://lore.kernel.org/lkml/20221010225342.3903590-1-ndesaulniers@google.com/)
    - `.fnstart` issue (reverted)
- [riscv LTO](https://lore.kernel.org/llvm/20220512205545.992288-1-twd2.me@gmail.com/) [CI](https://github.com/ClangBuiltLinux/continuous-integration2/issues/453)
- [website formatting for build matrix](https://github.com/ClangBuiltLinux/continuous-integration2/pull/454)
- rust, kcfi, kunit, and hardening updates for this merge window
- (Nathan) [riscv binutils interop bug](https://github.com/ClangBuiltLinux/linux/issues/1719) w/ DWARF
- `-gsplit-dwarf=single` might be interesting to use in the kernel
- clangd folks put a dent in top perf issue

## Sep 21, 2022
- Yonghong Song from Meta stopped by to discuss Meta using ClangBuiltLinux + [PGO](https://lore.kernel.org/linux-doc/20210407211704.367039-1-morbo@google.com/) in production at Meta as [alluded to at Linux plumbers conf](https://www.phoronix.com/news/Meta-Linux-Kernel-Live-Patching).
- Bill is seeking feedback on the ClangBuiltLinux Meetup, check your emails.
- PPC [xor autovectorization issue](https://github.com/ClangBuiltLinux/linux/issues/1713).
- Joao is working on [JCC tail calls to thunks in llvm](https://lore.kernel.org/llvm/Yv3uI%2FMoJVctmBCh@worktop.programming.kicks-ass.net/).
- overflow_kunit [issue](https://github.com/ClangBuiltLinux/linux/issues/1711).
- s390 qemu issue [fixed](https://github.com/ClangBuiltLinux/linux/issues/1709).
- kCFI [long tail fixes](https://github.com/ClangBuiltLinux/linux/issues/1705).
- Nathan has been fixing multiple -Wframe-larger-than= instances in AMDGPU. [0](https://github.com/ClangBuiltLinux/linux/issues/1681)[1](https://github.com/ClangBuiltLinux/linux/issues/1710)\
- Nick tracking register exhaustion blocking [Android toolchain upgrade](https://android-review.googlesource.com/c/kernel/common/+/2212595).
- ChromeOS dealing with [AutoFDO-related issues](https://lore.kernel.org/linux-arm-kernel/20220920082005.2459826-1-denik@chromium.org/) blocking their toolchain upgrade.
- Discussions being held about additional Rust and RISCV CI testing.
- 6.1 merge window to open in ~2-3 weeks
- Matthew Wilcox gave [a talk on 128b pointers at plumbers](https://www.youtube.com/watch?v=e2SZoUPhDRg&t=23063s).


## Sep 7, 2022
- CBL meetup is this weekend
- [plumbers is next week](https://lpc.events/event/16/)
  - [Toolchain Track is Wednesday](https://lpc.events/event/16/sessions/132/#20220914)
- [clang-15 has been released](https://discourse.llvm.org/t/llvm-15-0-0-release/65099)!
- (Nick) [fixing up](https://lore.kernel.org/lkml/20220907045907.484043-1-ndesaulniers@google.com/) debug info for asm, split debug info
- (Kees) [fixup for FORTIFY](https://lore.kernel.org/llvm/20220902204351.2521805-2-keescook@chromium.org/)
- (Bill) [ZERO_CALL_USED_REGS and paravirt](https://lore.kernel.org/all/20220902213750.1124421-3-morbo@google.com/)
- (Nick) `-Wformat` [back on](https://lore.kernel.org/lkml/20220901175913.2183047-1-ndesaulniers@google.com/)
- (Masahiro) [might be](https://lore.kernel.org/lkml/20220830190811.323760-1-masahiroy@kernel.org/) bumping binutils min version to 2.25.1
- (Nathan) [AMDGPU stack useage fixes](https://lore.kernel.org/llvm/20220830203409.3491379-1-nathan@kernel.org/)
- (Anders) [qemu boot timeouts](https://lore.kernel.org/all/20220906172257.2776521-1-alex.bennee@linaro.org/)
- (Craig) [div by constant](https://reviews.llvm.org/D130862)


## Aug 24, 2022
- (Saleem) fixing RISCV [regression](https://reviews.llvm.org/D132482)
- (Nick) asm goto cleanups
  - https://reviews.llvm.org/D130316
  - https://reviews.llvm.org/D130290
- (Nick) `-Wformat` cleanups
  - https://lore.kernel.org/CAHk-=wivP4zipYnwNWCLF5cd24GLs3m8=Sp7M-CmmPva_UC+3Q@mail.gmail.com/
  - https://reviews.llvm.org/D132266
  - https://reviews.llvm.org/D132568
  - https://lore.kernel.org/20220716084532.2324050-1-youngmin.nam@samsung.com/
- (Nathan) [Remove `-Wno-format-zero-length`](https://git.kernel.org/linus/370655bc183b1824ba623e621b58e8c2616c839c)
  - TODO: Enable [subflags of `-Wformat`](https://github.com/llvm/llvm-project/blob/dda38786534af733786c681e0c47b863e0626a0e/clang/include/clang/Basic/DiagnosticGroups.td#L934-L938) if `-Wno-format` is set
- (Nick) [remove CONFIG_CC_HAS_ASM_GOTO](https://lore.kernel.org/20220819190640.2763586-1-ndesaulniers@google.com/)
- (Nathan) chasing lots of `-Wsometimes-uninitialized` in -next ([issues](https://github.com/ClangBuiltLinux/linux/issues?q=is%3Aopen+label%3A-Wsometimes-uninitialized+label%3A%22%5BBUG%5D+linux-next%22))
- [`clang-15` in CI](https://github.com/ClangBuiltLinux/continuous-integration2/issues/387)
- (Nathan) [x86/build: Move '-mindirect-branch-cs-prefix' out of GCC-only block](https://lore.kernel.org/20220817185410.1174782-1-nathan@kernel.org/)
  - Required by [this series](https://lore.kernel.org/20211013122217.304265366@infradead.org/), which [landed in 5.16](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/?h=87c87ecd00c54ecd677798cb49ef27329e0fab41)
- (Nathan) [New instance of `-Wbitfield-constant-conversion`](https://lore.kernel.org/llvm/20220810010809.2024482-1-nathan@kernel.org/)

## Aug 10, 2022
- (Bill) Looking into reg stack clearing boot failure with paravirt
  - https://github.com/ClangBuiltLinux/linux/issues/1585
  - https://github.com/KSPP/linux/issues/192
  - https://reviews.llvm.org/D132073
- (Justin) [2.1% speedup](https://reviews.llvm.org/D131532) in build time
- (Craig) [dword division by constant](https://reviews.llvm.org/D130862)
  - Nick setup chat with Eli
- [riscv boot failure report](https://lore.kernel.org/bd14f1a2-750d-2511-df0a-85a9f5925f84@microchip.com/)
- ppc ftrace regression
  - [fixed](https://lore.kernel.org/llvm/20220809095907.418764-1-naveen.n.rao@linux.vnet.ibm.com/))
  - [reported by CKI](https://github.com/ClangBuiltLinux/linux/issues/1682)
- (Nick) [exec stack (BFD 2.39)](https://git.kernel.org/linus/0d362be5b14200b77ecc2127936a5ff82fbffe41)
- (Phoebe) [`-mindirect-branch-cs-prefix`](https://reviews.llvm.org/D130754)
  - Need kernel side fix to use this
- (Yuanfang) [UBSAN fix for setcc inline asm](https://reviews.llvm.org/D129954)
- (Nathan) [rewrote boot-utils in python](https://github.com/ClangBuiltLinux/boot-utils/pull/67)
- (Remi) [rewrote CI to use tuxsuite plans](https://github.com/ClangBuiltLinux/continuous-integration2/pull/395)
- [New AOSP clang](https://android-review.googlesource.com/c/kernel/common/+/2165482/)
  - Do we need to let tuxsuite know?
    - https://gitlab.com/Linaro/tuxmake/-/issues/193
- `clang-15` for CI
  - [tuxmake has it](https://gitlab.com/Linaro/tuxmake/-/issues/192), [tuxsuite needs it](https://gitlab.com/Linaro/tuxsuite/-/issues/171)
- [timetable for toolchain track at plumbers is live](https://lpc.events/event/16/sessions/132/#20220914)
  - Wednesday Sept 14 2022
- (Justin) [`-Wformat` should be headed to mainline](https://lore.kernel.org/20220720232332.2720091-1-justinstitt@google.com/) this merge window

## July 27, 2022
- (Nick) `blockaddress`/`callbr`
  - https://reviews.llvm.org/D130127
  - https://reviews.llvm.org/D130290
  - https://reviews.llvm.org/D130391
  - https://reviews.llvm.org/D130323
  - https://reviews.llvm.org/D130316
- (Justin) `-Wformat`
  - https://github.com/ClangBuiltLinux/linux/issues/378
  - https://lore.kernel.org/20220720232332.2720091-1-justinstitt@google.com/
- retbleed fixes / kcfi changes
  - https://lore.kernel.org/20220716230344.239749011@linutronix.de/
- mips 32b 64b o32
  - https://lore.kernel.org/CADVatmNtFYyqk0KwYzB1x6hOPkQ=0gV8mPN1BWp6QWrCs5GaxA@mail.gmail.com/
  - https://github.com/ClangBuiltLinux/linux/issues/884
  - https://llvm.org/pr38063
- X32
  - https://lore.kernel.org/20220701210437.579322-1-alex_y_xu@yahoo.ca/
  - https://lore.kernel.org/6cf4bab7-8c38-a2ee-07b9-fc95f901d2cb@kernel.org/
- llvm-15 release
  - https://github.com/ClangBuiltLinux/linux/issues/1678
- aeabi_ulmoddiv
  - https://github.com/ClangBuiltLinux/linux/issues/1666
  - https://github.com/llvm/llvm-project/issues/56153
- cbl meetup before plumbers
  - https://clangbuiltlinux.github.io/cbl-meetup/

## July 13, 2022
- [Retbleed](https://comsec.ethz.ch/research/microarch/retbleed/)
  - (Nick) [llvm patch](https://reviews.llvm.org/D129572)
  - (Nathan) [0day randconfig fix](https://lore.kernel.org/llvm/20220713152436.2294819-1-nathan@kernel.org/)
  - (Nathan) [reported issue with sanitizers](https://github.com/llvm/llvm-project/issues/56514)
    - https://github.com/llvm/llvm-project/commit/a88c722e687e6780dcd6a58718350dc76fcc4cc9
  - Nick will be focused on LLVM backports for Android, need help from testers to report issues
  - backports queued back to 5.10.y, Nick needs to know if 5.4 or older is attempted
- (Nick) [coresight patch picked up](https://lore.kernel.org/lkml/20220708231520.3958391-1-ndesaulniers@google.com/)
  - (Arnd) mentioned its probably better to fix this differently in the long run, perhaps "i" constrained inputs to inline asm
- (Fangrui) implement -mrelax on lld!
  - [kernel patch](https://lore.kernel.org/llvm/20220710071117.446112-1-maskray@google.com/)
  - [llvm impl](https://github.com/llvm/llvm-project/commit/6611d58f5bbcbec77262d392e2923e1d680f6985)
  - [llvm fixup](https://github.com/llvm/llvm-project/commit/6b1d151fe3dc530195d8802f1ecc247c8235dd3a)
- (Justin) lots of -Wformat fixes, time to remove -Wno-format for clang?
- [callbr rework](https://reviews.llvm.org/D129288), need time to test
- [`-mstack-protector-guard-symbol`](https://reviews.llvm.org/D129346)
- (Peter) is function attribute "keep" arch specific?
  - (Nick) [Yes](https://godbolt.org/z/8Ke3Yaz51)
- [ubsan divide by zero](https://github.com/ClangBuiltLinux/linux/issues/1657), need to disable this config for clang for now
- (Arnd) x86-64-v2 might be a good minimum target for static clang builds

## June 29, 2022
- Patches for gen_compile_commands [1](https://lore.kernel.org/llvm/20220628012353.13995-1-jhubbard@nvidia.com/)[2](https://lore.kernel.org/llvm/20220628122741.93641-2-daniel.thompson@linaro.org/)
- (Nick) [axe CONFIG_CC_OPTIMIZE_FOR_PERFORMANCE_O3](https://lore.kernel.org/linux-kbuild/20220628210407.3343118-1-ndesaulniers@google.com/)
- (Nick) [coresight fix for UBSAN_TRAP](https://lore.kernel.org/llvm/20220623174131.3818333-1-ndesaulniers@google.com/)
- (Nick) [issue with objtool fallthough](https://github.com/ClangBuiltLinux/linux/issues/1657)
- (Nick) [`-Wunused-but-set-variable` building perf](https://github.com/ClangBuiltLinux/linux/issues/1654)
- (Nick) PGO done for static clang, but musl profiles hurt perf
- (Nathan) [fix for downstream incfs](https://android-review.googlesource.com/c/kernel/common/+/2134978/)
- (Nathan) [sigpipe with `grep -q`](https://github.com/ClangBuiltLinux/linux/issues/1651)
- (Nathan) [chasing cros ci build timeouts](https://github.com/ClangBuiltLinux/continuous-integration2/pull/383)
- (Nathan) lld-11 breakage in -next
- (Arnd) need musl cross libs for hostcc
- (Tom) gcc target triples aren't necessarily the same behavior for clang
- (Tom) fedora links with -z,now
  - Upstream link against libclang-cpp.so
  - PGO experiments
- (Justin) `-Wformat` warning fixes


## June 15, 2022
- CBL Meetup [attend form](https://forms.gle/iCkYRyUqi2Bd26YN9)
- [LLVM Bay Area Monthly Meetup](https://discourse.llvm.org/t/llvm-bay-area-monthly-meetup-mon-july-11-22-6pm/63193) (Mon July 11 '22 6pm)
- (Nick) [Coresight assembler issue v4](https://lore.kernel.org/llvm/20220614220229.1640085-1-ndesaulniers@google.com/)
- (Nathan) container builds ported to [self hosted actions](https://github.com/ClangBuiltLinux/containers/pull/25), [aarch64 host builds](https://github.com/ClangBuiltLinux/containers/pull/29) working.
- (Justin) `-Wformat` fixes [0](https://lore.kernel.org/llvm/20220607191119.20686-1-jstitt007@gmail.com/)[1](https://lore.kernel.org/llvm/20220607180847.13482-1-jstitt007@gmail.com/)[2](https://lore.kernel.org/llvm/20220608223539.470472-1-justinstitt@google.com/) 
- (Nick) toolchain
  - TODO: is there an s390 gnu binutils multiarch package on alpine?
    - [Yes](https://pkgs.alpinelinux.org/package/edge/testing/x86_64/binutils-s390x)
- (Nathan) [testing ChromeOS kernels again](https://github.com/ClangBuiltLinux/continuous-integration2/pull/376)
- [CI patch application failing](https://gitlab.com/Linaro/tuxsuite/-/issues/169)
- (Mark) [kselftest cross compilation wired up](https://lore.kernel.org/llvm/20220614121045.1046475-1-broonie@kernel.org/)
- (Nathan) `-Wframe-larger-than` in [sound/soc/intel/avs/path.c](https://github.com/ClangBuiltLinux/linux/issues/1642)
- `__aeabi_uldivmod` in [drivers/mtd/parsers/scpart.o](https://github.com/ClangBuiltLinux/linux/issues/1635)

## June 1, 2022
- (Phoebe) x86 [SLS patch](https://reviews.llvm.org/D126137) landed
- (Nick) kernel.org toolchain work
- (Nathan) [s390 LLVM_IAS=1 in ci](https://github.com/ClangBuiltLinux/continuous-integration2/pull/367)
- (Nick) ARCH=arm `-Wunused-command-line` [will need compiler change]([url](https://lore.kernel.org/llvm/CAKwvOdmkd2PxvMUZA=A-72eATGDZkqDj--Bv1W+Xt_K_LWdROA@mail.gmail.com/)).
- (Nathan) [libvert blog post](https://nathanchance.dev/posts/github-actions-fedora-libvirt/)
- build timeouts?
- (Kees) BOS
  - https://github.com/llvm/llvm-project/issues/55741
  - https://github.com/llvm/llvm-project/issues/55742
- ppc vdso lld patch is merged, LTO next?
- merge window open
  - riscv asm patch needed
- meetups (CBL & Plumbers)
- loongarch did the llvm patches go in?
  - [yes](https://github.com/llvm/llvm-project/commits/main/llvm/lib/Target/LoongArch)

## May 18, 2022
- [LTO for riscv](https://lore.kernel.org/llvm/20220512205545.992288-1-twd2.me@gmail.com/)
- cbl meetup 3 [location](https://clangbuiltlinux.github.io/cbl-meetup/)
- plumbers [location](https://lpc.events/)
- (Nick) ARCH=arm [-Wunused-command-line](https://lore.kernel.org/llvm/20220516210954.1660716-1-ndesaulniers@google.com/)
- (Nick) [statically linked clang image](https://github.com/ClangBuiltLinux/containers/pull/5) for kernel.org
- [regression](https://lore.kernel.org/linux-hardening/20220511174531.1098548-1-keescook@chromium.org/) from 64b div on 32b arm for old versions of clang.
  - Dropped
- (Nathan) working towards [enabling](https://github.com/ClangBuiltLinux/continuous-integration2/pull/366) chromeos kernel config testing in ci
- [390 LLVM_IAS patches](https://lore.kernel.org/lkml/20220511120532.2228616-1-hca@linux.ibm.com/), LTO next?
  - (Nathan) [wire up CI support](https://github.com/ClangBuiltLinux/continuous-integration2/pull/367)
- (Nick) fixed [blocker](https://reviews.llvm.org/D125285) for removing `-ffreestanding` from i386, for FORTIFY_SOURCE
- download url blank for some tuxsuite builds
- (Nathan) [ppc vdso LLD fixes](https://lore.kernel.org/llvm/20220509204635.2539549-1-nathan@kernel.org/)
- [interesting builtin patches](https://lore.kernel.org/llvm/20220510142550.1686866-2-mailhol.vincent@wanadoo.fr/)
- riscv 9th arg calling convention [issue reported](https://lore.kernel.org/llvm/20220510065336.hlfjrc25ajed5zj4@M910t/)
- (Bill) [AArch64 Add support for -fzero-call-used-regs](https://reviews.llvm.org/D124836)
- objtool regression, [patch pending](https://github.com/ClangBuiltLinux/linux/issues/1639#issuecomment-1129465068)
- [arm eabi -next regression](https://github.com/ClangBuiltLinux/linux/issues/1635)
- (Mark) clang cross compile kselftest doesn't work correctly

## May 4, 2022
- [kCFI](https://lore.kernel.org/llvm/20220429203644.2868448-1-samitolvanen@google.com/)
- LTO for [ppc64le](https://lore.kernel.org/llvm/20220429064547.2334280-1-aik@ozlabs.ru/) and [arm](https://github.com/ClangBuiltLinux/linux/issues/1627)
- [`-fzero-call-used-regs`](https://reviews.llvm.org/D124836)
- [randstruct](https://lore.kernel.org/llvm/20220503205503.3054173-1-keescook@chromium.org/)
- [KMSAN](https://www.phoronix.com/scan.php?page=news_item&px=KernelMemorySanitizer-2022)
- [cbl meetup 3 CFP](https://lore.kernel.org/llvm/CAGG=3QX8M0p2JQOs6tq0ZSqHKLhzVh77eCxYkh22SDL6Qaa36g@mail.gmail.com/)

## Apr 20, 2022
- (Bill) [randstruct in phoronix](https://www.phoronix.com/scan.php?page=news_item&px=Clang-Linux-RandStruct)
- (Sami) [kCFI](https://reviews.llvm.org/D119296)
- (Joao) [`-mibt-seal`](https://reviews.llvm.org/D118052)
- (Joao) [Fine IBT support](https://lore.kernel.org/linux-hardening/20220420004241.2093-1-joao@overdrivepizza.com/)
- (Nick) Plumbers planning
- (Nick) finally [fixed LTO blockaddress issue in llvm](https://reviews.llvm.org/D120781)
- (Nick) Paperwork on restarting LLVM Bay Area Meetup
- (Nick) LLVM+BOLT [kernel measurements](https://lore.kernel.org/llvm/CAKwvOdm08hr2p-ARqmPEGnCi6zZOtgmt5d45hYG2vo30mhyMrg@mail.gmail.com/)
- (Nick) `-ffreestanding` on i386 [higher priority](https://lore.kernel.org/llvm/CAKwvOdkQeSx3uy25KaTrX=ywc26wDEefXHbCB_ifGot+yXGvHQ@mail.gmail.com/)
- (Bill) [Meetup CBL](https://clangbuiltlinux.github.io/cbl-meetup/)
- (Nick) docker image in the works
- (Tom) [new llvm release cycle](https://discourse.llvm.org/t/llvm-14-0-1-schedule-and-release-updates/61227)

## Apr 6, 2022
- (Bill) [randstruct](https://reviews.llvm.org/D121556)
- (Nathan) [`ARCH=um` in CI](https://github.com/ClangBuiltLinux/boot-utils/pull/59)
- (Nick) `CONFIG_UAPI_HEADER_TEST=y` with bionic sysroot, Masahiro agrees we should pursue `-nostdinc`.
- (Nathan) `-Wdeclaration-after-statement` kernel fix
- (Sami) [cfi aarch64 `__builtin_function_start`](https://lore.kernel.org/lkml/20220401201916.1487500-1-samitolvanen@google.com/)
- (Joao) [`-mibt-seal` LTO](https://reviews.llvm.org/D118052)
- [`-Wno-gnu` fixes](https://reviews.llvm.org/D122224)
- (Nathan) [aarch64 qemu FEAT_LPA](https://github.com/ClangBuiltLinux/boot-utils/pull/61)
- (Nathan) debugging paravirt -fzero-call-saved
- Meetup Date Sept 10-11, announcement posts incoming, CFP too. Dublin, Ireland.
- https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.18-More-Flexible-LLVM

## Mar 23, 2022
- bootconfig LTO [issue reported](https://lore.kernel.org/linux-doc/164724892075.731226.14103557516176115189.stgit@devnote2/).
- [llvm-14 released](https://github.com/llvm/llvm-project/releases/tag/llvmorg-14.0.0).
- 5.18 merge window is open
  - `-std=gnu11` change in Kbuild tree, PR not yet sent.
    - `-Wdeclaration-after-statement` [fixed](https://github.com/ClangBuiltLinux/linux/issues/1603) in `arm_neon.h` ARCH=arm BE in clang-15, need kernel fix
- (Nick) Android CONFIG_UAPI_HEADER_TEST w/ Bionic sysroot WIP, Android kernel toolchain upgrade
- ARCH=um support! Nathan [wiring up](https://github.com/ClangBuiltLinux/continuous-integration2/pull/337) CI coverage and [boot-utils](https://github.com/ClangBuiltLinux/boot-utils/pull/59).
- (Bill) `__builtin_read_eflags` DOA.
- (Bill) `-Wformat` patches in the works.
- (Bill) randstruct work refreshed.
- (Bill) [cr4/0 pinning](https://github.com/KSPP/linux/issues/19)
- CFP season (plumbers MC CFP, Kernel security, EuroLLVM).
- More kernel IBT discussions with Intel.
  - João Moreira has done a lot of research in the area.
    - [DROP THE ROP: Fine-grained Control-flow Integrity for the Linux Kernel](https://www.blackhat.com/docs/asia-17/materials/asia-17-Moreira-Drop-The-Rop-Fine-Grained-Control-Flow-Integrity-For-The-Linux-Kernel-wp.pdf)
    - [Fine-grained Forward CFI on top of Intel CET / IBT](https://www.openwall.com/lists/kernel-hardening/2021/02/11/1)
    - [Hardware-Assisted Fine-Grained Control-Flow Integrity: Adding Lasers to Intel’s CET/IBT](https://static.sched.com/hosted_files/lssna2021/8f/LSS_FINEIBT_JOAOMOREIRA.pdf)
  - https://github.com/intel/fineibt_glibc/commits/fineibt
  - https://github.com/samitolvanen/llvm-project/commits/kcfi
- clangify-glibc https://sourceware.org/git/?p=glibc.git;a=shortlog;h=refs/heads/azanella/clang 

## Mar 9, 2022
- Spectre-BHB fallout
  - (Nathan) aarch64+LTO [header inclusion issue](https://lore.kernel.org/llvm/20220309191633.2307110-1-nathan@kernel.org/)
  - (Nathan) arm semicolon
  - arm [lld error](https://github.com/ClangBuiltLinux/linux/issues/1609)
  - [arm operand](https://github.com/ClangBuiltLinux/linux/issues/1610)
- (Nick) ["Never resolved function from blockaddress"](https://github.com/llvm/llvm-project/issues/52787) [fix](https://reviews.llvm.org/D120781)
- [`-std=gnu11`](https://lore.kernel.org/linux-kbuild/20220308215615.14183-1-arnd@kernel.org/) early 5.18 merge window
- (Nathan) [make LLVM= more flexible](https://lore.kernel.org/linux-kbuild/20220304170813.1689186-1-nathan@kernel.org/)
- CONFIG_UAPI_HEADER_TEST
  - [set `--target=`](https://lore.kernel.org/linux-kbuild/20220305125605.149913-1-masahiroy@kernel.org/)
  - [allow `--sysroot`](https://lore.kernel.org/linux-kbuild/20220201213542.2808035-1-quic_eberman@quicinc.com/)
- `__diag` support
- (Fangrui) [ppc lld fix](https://lore.kernel.org/all/20220309055118.1551013-1-maskray@google.com/)
- (Nick) mips sp register
- [GCC added SCS support](https://lore.kernel.org/lkml/20220303073340.86008-1-ashimida@linux.alibaba.com/) :)
- [x86 IBT working with clang](https://lore.kernel.org/lkml/20220308153011.021123062@infradead.org/)
- tuxrun WIP, might be nice to have musl to cross compile various tests for

## Feb 23, 2022

- [`(NOLOAD)` error/warning](https://github.com/ClangBuiltLinux/linux/issues/1597)
- [`__alloc_size(1)` issue with `__kmalloc_track_caller`](https://github.com/ClangBuiltLinux/linux/issues/1599)
- NULL pointer dereference in `net/core/rtnetlink.c`:
  - [Upstream thread](https://lore.kernel.org/r/Yg2h2Q2vXFkkLGTh@dev-arch.archlinux-ax161/)
  - [CBL issue](https://github.com/ClangBuiltLinux/linux/issues/1594)
- Continuous integration [now supports `clang-14`](https://github.com/ClangBuiltLinux/continuous-integration2/pull/304) after [workflow split](https://github.com/ClangBuiltLinux/continuous-integration2/pull/302)
- [Support for `ARCH=um`](https://lore.kernel.org/r/20220217002843.2312603-1-keescook@chromium.org/)
- [Mitigating kernel risks on 32-bit ARM](https://security.googleblog.com/2022/02/mitigating-kernel-risks-on-32-bit-arm.html)
- [GCC warnings with `-std=gnu11`](https://lore.kernel.org/r/CAHk-=wgLe-OSLTEHm=V7eRG6Fcr0dpAM1ZRV1a=R_g6pBOr8Bg@mail.gmail.com/), [clang does not warn](https://github.com/llvm/llvm-project/commit/59802321785b4b9fc31b10456c62ba3a06d3a631) due to `-fno-strict-overflow`, which implies `-fwrapv`, which makes signed integer overflow "defined"

## Feb 9, 2022
- (Kees) FORTIFY_SOURCE [clang patches](https://lore.kernel.org/llvm/20220208225350.1331628-1-keescook@chromium.org/)
  - (Nick) ARCH=i386 [kinda depends on](https://github.com/ClangBuiltLinux/linux/issues/1583) `-ffreestanding` atm 
- (Sami) kCFI clang [patch posted](https://reviews.llvm.org/D119296)
 - TODO: llvm patches for x86 Ibt
- (Nathan) has good summaries for enabling CONFIG_WERROR for [arm64](https://github.com/ClangBuiltLinux/continuous-integration2/issues/246#issuecomment-1033048610) and [x86](https://github.com/ClangBuiltLinux/continuous-integration2/issues/245#issuecomment-1033100464)
  - in particular [DMA_BIT_MASK](https://git.kernel.org/pub/scm/linux/kernel/git/hyperv/linux.git/commit/?id=6bf625a4140f24b490766043b307f8252519578b) patch kind of deprioritizes https://github.com/ClangBuiltLinux/linux/issues/92 again.
- (Bill) landed [initial support](https://reviews.llvm.org/D110869) for `-fzero-call-used-regs` [option](https://github.com/ClangBuiltLinux/linux/issues/20)
- (Nick) [a fix](https://git.kernel.org/pub/scm/linux/kernel/git/jpoimboe/linux.git/commit/?h=objtool/urgent&id=bfb1a7c91fb7758273b4a8d735313d9cc388b502) for objtool warnings for configs that set `-march`
- (Nick) rebased [eflags patch](https://reviews.llvm.org/D92695), still don't really understand redzone concerns.
- (Nick) chasing [a clang-14+ objtool warning](https://github.com/ClangBuiltLinux/linux/issues/1563)
- [ppc lld boot regression](https://github.com/ClangBuiltLinux/linux/issues/1581)
- ideas for intern project?
- meetup?
- (Arnd) -ffreestanding per arch may have just needed to be on lib/string.h (only 4 are x86, mips, xtensa, m68k)
  - mips mentions something in additon to string.h functions 
- (Arnd) 10% build time improvement by making atomics extern functions rather than macros
- plumbers 2022 will be in Dublin, [uConf CFP is open](https://lpc.events/event/16/abstracts/)

## Jan 26, 2022
- (Ard) [fixups](https://lore.kernel.org/linux-arm-kernel/20220125153656.1802079-1-ardb@kernel.org/) for ARCH=arm ftrace
- (Nick) focused on [objtool warnings](https://github.com/ClangBuiltLinux/linux/issues/1566) regarding `asm volatile`
  - Probably going to add -Wasm-volatile to warn when `volatile` does nothing (ie. `asm goto` or no outputs)
- Met with Intel to discuss kernel IBT, PeterZ has [patches](https://git.kernel.org/pub/scm/linux/kernel/git/peterz/queue.git/log/?h=x86/wip.ibt)
- (Sami) working on ["kcfi"](https://github.com/samitolvanen/llvm-project/commits/kcfi)
- CFI [issue reported](https://github.com/ClangBuiltLinux/linux/issues/1567) with blake2s
- issue with [false positive warnings on globals](https://github.com/ClangBuiltLinux/linux/issues/92) coming up again.
- sysroot
- arnd header cleanup randconfigs for ARCH=arm ARCH=arm64 1.7x speedup with clang
- [clang noundef analysis](https://github.com/ClangBuiltLinux/linux/issues/1480)
- CrOS analysing [most used headers](https://commondatastorage.googleapis.com/chromium-browser-clang/llvm_includes-index.html) in LLVM
- Kees' [LCA talk](https://www.youtube.com/watch?v=17Nqwl30Ch0)
- [`-Wshorten-64-to-32`](https://twitter.com/kees_cook/status/1485757844322340864)

## Jan 12, 2022
- (Nick) [asm goto fixes](https://github.com/llvm/llvm-project/commits?author=nickdesaulniers&since=2022-01-01&until=2022-01-15)
- [issue](https://github.com/ClangBuiltLinux/linux/issues/1566) reported with asm volatile?
  - maybe the same issue as [this](https://github.com/ClangBuiltLinux/linux/issues/1483) or [this](https://github.com/ClangBuiltLinux/linux/issues/679#issuecomment-910865782)/[this](https://github.com/ClangBuiltLinux/linux/issues/621)
- [no_stack_protector + always_inline changing](https://reviews.llvm.org/D116589), likely to resurface issues with LTO + suspend/resume
- \__attribute__(deallocator) [clang feature request](https://github.com/llvm/llvm-project/issues/53152)
- Need to focus on [global warnings](https://github.com/ClangBuiltLinux/linux/issues/92) again
- LLD feature request for "pass through" of sections for -ffunction-sections -fdata-sections
  - Should be filed as a feature request to gnu binutils
    - [Done](https://sourceware.org/bugzilla/show_bug.cgi?id=28772)
  - https://maskray.me/blog/2020-11-15-explain-gnu-linker-options#z-unique-symbol
- Ingo's fast header series
  - `-dM with -E` together or differenced? 
- Linux Conf AU coming up, see [Kees' talk](https://linux.conf.au/schedule/presentation/27/)

## Dec 29, 2021
- probably will be an -rc8 release to delay 5.16 until after new years.
- (Alexey) ARCH=powerpc LLVM_IAS=1 [patches](https://lore.kernel.org/llvm/20211221055904.555763-1-aik@ozlabs.ru/)
- (Ard) [XOR_NEON](https://github.com/ClangBuiltLinux/linux/issues/496) fixes in the works (marking parameters as `__restrict`)
- (Ard) [out of range fixup](https://github.com/ClangBuiltLinux/linux/issues/1551)
- (Nathan) [clang fix for -mno-outline-atomics](https://reviews.llvm.org/D116128)
- (Nathan) updated bugzilla links to github
- (Nathan) [Adding Links to Issues](https://github.com/ClangBuiltLinux/linux/wiki/Adding-links-to-issues)
- (Nick) asm goto fixes
  - https://reviews.llvm.org/D115688
  - https://reviews.llvm.org/D115410
  - https://reviews.llvm.org/D115311
  - https://reviews.llvm.org/D115471
  - https://reviews.llvm.org/D116059
- a few new LTO bugs filed
  - https://github.com/ClangBuiltLinux/linux/issues/1559
  - https://github.com/ClangBuiltLinux/linux/issues/1556
  - https://github.com/ClangBuiltLinux/linux/issues/1554
  - https://github.com/ClangBuiltLinux/linux/issues/1550
- (Bill) [builtin eflags](https://lore.kernel.org/llvm/20211229021258.176670-1-morbo@google.com/)
- hyperv tickling https://github.com/ClangBuiltLinux/linux/issues/92#issuecomment-998099643.
- (Nathan) playing with containers for boot testing

## Dec 15, 2021
- GKH stopped by to say hello
  - ARCH=arm allmodconfig warnings making it difficult to enable CONFIG_WERROR
  - https://github.com/ClangBuiltLinux/linux/issues/496
- LLVM issue tracker has moved from [bugzilla](https://bugs.llvm.org/) to [github](https://github.com/llvm/llvm-project/issues)
  -  [kernel meta bug](https://github.com/llvm/llvm-project/issues/4440)
  -  Issue numbers aren't 1:1
    -  You can visit llvm.org/PRXXXX where XXXX is the OLD PR number to get redirected to the new github issue number, ie. [llvm.org/PR4068](https://llvm.org/PR4068)
  - We should:
    - update [our bug tracker](https://github.com/ClangBuiltLinux/linux/issues) links
    - update [links in kernel source](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/)
    - update [links in LLVM source](https://github.com/llvm/llvm-project)
- (Nathan) [LTO breakage with .macro redefinitions](https://github.com/ClangBuiltLinux/linux/issues/1513) [fixed](https://lore.kernel.org/lkml/20211210234953.3420108-1-nathan@kernel.org/)
- (Nathan) [Change TuxSuite targets](https://github.com/ClangBuiltLinux/continuous-integration2/pull/256)
- [MIPS LTO support](https://lore.kernel.org/lkml/20211213224914.1501303-1-paul@crapouillou.net/)
  - Asks about ARCH=arm LTO
- [whole bunch of new mips bugs filed recently](https://github.com/ClangBuiltLinux/linux/issues?q=is%3Aissue+is%3Aopen+label%3A%22%5BARCH%5D+mips%22)
- (Marco) [`-ftrivial-auto-var-init=` and allocas](https://reviews.llvm.org/D115440)
- (Kees) [deprecating -fsanitize=object-size](https://lore.kernel.org/r/20211203235346.110809-1-keescook@chromium.org/)
- (Nick) [asm goto w/ outputs breakage with "+r" constraints](https://github.com/ClangBuiltLinux/linux/issues/1512) - [fix updated](https://reviews.llvm.org/D115688)
  - Probably going to look at https://github.com/ClangBuiltLinux/linux/issues/1439 next.
- (Nick) Android work
  - Upgrading kernel toolchain
  - minimizing `make` invocation for Android T
  - VTS tests
  - u-boot 32b ARM+LLD
- [RISC-V relocation R_RISCV_HI20 out of range with CONFIG_CMODEL_MEDLOW=y](https://github.com/ClangBuiltLinux/linux/issues/1533)
- (Arnd) unaligned access (siphash?) (Ard has a draft reply) `CONFIG_UBSAN_ALIGNMENT`+`HAVE_EFFICIENT_UNALIGNED_ACCESS`
- (Arnd) header file dependencies - Linus had feedback
- [interesting glibc abi project](https://github.com/ziglang/glibc-abi-tool)
  - reminiscent of [tendra](http://www.tendra.org/)?

## Dec 1, 2021
- (Nathan) [Reducing an LTO Linux kernel bug with cvise](https://nathanchance.dev/posts/cvise-lto-kernel-bug/)
- (Nathan) [raise llvm min version to 11](https://lore.kernel.org/llvm/20211129165803.470795-2-nathan@kernel.org/)
- (Bill) [asm goto -Wunitialized](https://github.com/ClangBuiltLinux/linux/issues/1521) - [fix](https://reviews.llvm.org/D69868)
- (Nick) [asm goto w/ outputs breakage with "+r" constraints](https://github.com/ClangBuiltLinux/linux/issues/1512) - [fix](https://reviews.llvm.org/D114895)
- (Nick) [arm32 stack guard CrOS test failure](https://bugs.chromium.org/p/chromium/issues/detail?id=1270361) - [fix](https://reviews.llvm.org/D114762)
- (Phoebe) [re-enabling float/double support even for -mno-x87](https://reviews.llvm.org/D114162)
- [LTO breakage with .macro redefinitions](https://github.com/ClangBuiltLinux/linux/issues/1513)

## Nov 17, 2021
- (Maz) [CFI breakage](https://github.com/ClangBuiltLinux/linux/issues/1503)
- (Nathan) [Long double literals](https://github.com/ClangBuiltLinux/linux/issues/1497)
- [Time to upgrade to clang-11?](https://github.com/ClangBuiltLinux/linux/issues/1506)
  - https://github.com/ClangBuiltLinux/misc-scripts 
- (Nick) [patch for armv6 hard thread pointer](https://github.com/ClangBuiltLinux/linux/issues/1502)
- (Nathan) linux-5.15.y [CI coverage wired up](https://github.com/ClangBuiltLinux/continuous-integration2/pull/240)
- (Phoebe) [-mno-fp-ret-in-387](https://reviews.llvm.org/D112143), [-mskip-rax-setup](https://reviews.llvm.org/D112413)
- (Ulrich) commented on open s390 LLVM_IAS=1 bugs, Ilie sent [a patch](https://lore.kernel.org/lkml/20211117174822.3632412-1-ilie.halip@gmail.com/)
- (Anders) has been sending patches fixing warnings from the kselftests
- Interesting thread: [RFC: adding support to GCC for detecting trust boundaries](https://lore.kernel.org/linux-toolchains/20211113203732.2098220-1-dmalcolm@redhat.com/)
- [LLVM dev meeting](https://llvm.swoogo.com/2021devmtg/)
- (Arnd) mentioned build time regression on IRC
- Sami's x86_64 mainline CFI branch red
  - https://git.kernel.org/linus/2105a92748e83e2e3ee6be539da959706bbb3898
- (Tom) BUILD_BUG -> \_Static_assert and typeof(x) -> \_\_auto_type clang-tidy

## Nov 3, 2021
- (Serge) [LTO+FORTIFY](https://github.com/ClangBuiltLinux/linux/issues/1477) [fix](https://reviews.llvm.org/D112059) has landed in LLVM.
- [GCC SCS aarch64 WIP](https://lore.kernel.org/linux-hardening/20211102075812.122715-1-ashimida@linux.alibaba.com/)
- (Ard) Working on 32b ARM per task stack canaries [0](https://reviews.llvm.org/D112600), [1](https://reviews.llvm.org/D112811), [2](https://reviews.llvm.org/D113026), [3](https://reviews.llvm.org/D112768), [3](https://lore.kernel.org/linux-arm-kernel/20211028083527.1057158-1-ardb@kernel.org/).
- (Phoebe) x86 llvm patches for [-mno-fp-ret-in-387](https://reviews.llvm.org/D112143), [-mskip-rax-setup](https://reviews.llvm.org/D112413), and [-maccumulate_outgoing_args](https://reviews.llvm.org/D112415).
- Removing CROSS_COMPILE_COMPAT causing issues for Linaro TCWG CI since they disable 32b arm support in llvm for their 64b arm kernel builds.
  - `clang -print-targets`
- Met with Nemanja and Sean at IBM regarding PPC. MPE@ couldn't make it this week, but perhaps next time due to timezone changes in AU.  MPE mentions via IRC "we're a bit wedged on the EFLv2 ppc64be thing, because the gcc/binutils folks *don't* support it"
- Met with Intel
  - Need to find out more about [SLS](https://www.phoronix.com/scan.php?page=news_item&px=Straight-Line-Speculation-x86) 
- LLVM Bay Area meetup went well. Nick presented about CBL; mostly folks unaware of the project asking basic questions.
  - LLVM meetup coming up in two weeks, register now
- Android specific perf tests? Binder throughput tests.
- CFI redesign x86 questions on LKML / Aarch64 static calls blocked by CFI issue related to asm labels on declarations in C.

## Oct 20, 2021
- Lots of patches around `-Wbitwise-instead-of-logical`, Linus not thrilled with note diagnostic.
- (Nick) [eliminated](https://lore.kernel.org/lkml/20211019223646.1146945-2-ndesaulniers@google.com/) CROSS_COMPILE_COMPAT for LLVM=1 arm64 compat vdso.
- (Serge) [fix](https://reviews.llvm.org/D112059) for [LTO+FORTIFY](https://github.com/ClangBuiltLinux/linux/issues/1477).
- arm64 `.cfi_negate_ra_state`+PAC [LLVM patch](https://reviews.llvm.org/D111780).
- (Nick) thinLTO+CFI .cfi_jt fixup [LLVM patch](https://reviews.llvm.org/D107934).
- (Ard) arm32 [IRQ stacks](https://lore.kernel.org/linux-arm-kernel/20211017131723.4034662-1-ardb@kernel.org/) and [vmapped stacks](https://lore.kernel.org/linux-arm-kernel/20211018141615.682070-1-ardb@kernel.org/).
  - regression in next `__eabi_read_tb`
- (Nick) working on [propagating tail calls](https://reviews.llvm.org/D107872) for fortify.
- 32b [unwinder fixes](https://lore.kernel.org/linux-arm-kernel/163369614818.636038.5019945597127474028.stgit@devnote2/) for kprobes.
- (Miguel) [mark](https://lore.kernel.org/lkml/20211014132331.GA4811@kernel.org/) `__compiletime_assert` `noreturn`.
- [MPE](https://lore.kernel.org/linuxppc-dev/20211014024424.528848-1-mpe@ellerman.id.au/) and Nemanjai looking into LLVM_IAS=1 for ppc.
- (Rasmus) [switch container_of from BUILD_BUG_ON to static_assert](https://lore.kernel.org/lkml/20211015090530.2774079-1-linux@rasmusvillemoes.dk/).
- kasan excessive stack useage, [interesting case](https://godbolt.org/z/P3qb4nGYe) fron Arnd.
  - `-fno-sanitize-address-use-after-scope` and `-fsanitize-address-use-after-return=never` (gcc's `--param asan-use-after-return=1`)
  - large padding for small locals?
- LLVM bay area meetup tonight. 5pm CBL round table.
  - ppc & s390 assembler, kasan stack useage, ARC + m68k
- atom cpu tuning is bad; leads to frequent register exhaustion. (TODO: Nick, talk to Intel): https://github.com/ClangBuiltLinux/linux/issues/1483
- rust tentative clang flags removed from rustforlinux kbuild modifications
- https://github.com/ClangBuiltLinux/linux/issues/1315: argument unused during compilation: '-march=armv6k' #1315

## Oct 6, 2021
- Meeting notes moved to github
- [Meetup in Oct](https://www.eventbrite.com/e/bay-area-llvm-developers-meetup-tickets-173682136947)
- (Nick): Working on https://github.com/ClangBuiltLinux/linux/issues/1302 in LLVM.
- BLK_DEV_NBD issue all resolved https://github.com/ClangBuiltLinux/linux/issues/1438
- (Serge, Nick): small fixes for inline https://reviews.llvm.org/D111009, https://reviews.llvm.org/D107872
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
  - Bill describing difficulties in implementation of zeroing callee used regs.
  - Plumbers (Toolchain MC Friday)
  - Almost back to green in CI now that we can apply patch files
    - TODO: re-enable -Werror for allmodconfig builds
    - [Arnd’s randconfig W=1 builds almost green for GCC and Clang](https://git.kernel.org/pub/scm/linux/kernel/git/arnd/playground.git/log/?h=randconfig-5.15-min) 
    - Kees had QEMU buffering fixes for ci
  - Nick bootstrapping llvm against musl
  - https://reviews.llvm.org/D109837
    - Try -DLLVM_HOST_TRIPLE=


## Sep 8, 2021
  - [Need attribute error warning kernel fixes to be picked up by Miguel](https://github.com/ClangBuiltLinux/linux/issues/1173)
  - [__mulodi4 llvm fixes in, need to do kernel fixes](https://github.com/ClangBuiltLinux/linux/issues/1438)
    - Todo file bug against gcc for mulodi4?
  - [Switch bit test fixes landed in llvm fixes LTO boot](https://reviews.llvm.org/rG4331f19d8b9ac8101d55073834b35814afce4e5a)
  - [-Werror](https://lore.kernel.org/lkml/20210907183843.33028-1-ndesaulniers@google.com/)
  - Sanitizer vs frame-larger-than=
  - Stable vs compiler version checks
    - TODO Disable WERROR in CI
  - LLVM_IAS=1 CROSS_COMPILE landed in mainline
  - 5.15 merge window open 
  - Conf cfps
    - [Distributors conf](https://github.com/ClangBuiltLinux/llvm-distributors-conf-2021/issues)
    - [CBL meetup 2](https://github.com/ClangBuiltLinux/CBL-meetup-II-turbo/issues)
    - [LinuxConfAU extended their deadline](https://linux.conf.au/programme/miniconfs/)
    - [LLVM virtual meetup (no BoFs this year, let's do a roundtable?)](https://lists.llvm.org/pipermail/llvm-dev/2021-September/152483.html)
  - Kasan s390 ci coverage added to our CI
    - Nearing Github Actions CI matrix limit
  - Kees fortify patches (being split into 2 series)
  - New mailing list and IRC
    - TODO update mailmap
    - llvm@lists.linux.dev
    - #clangbuiltlinux on irc.libera.chat
  - Sami CFI patches
    - https://reviews.llvm.org/D108478
    - https://reviews.llvm.org/D108479
  - [Bill finding shadowing and scev issues](https://reviews.llvm.org/D104741)
    - b/198158061 
  - Talk to Miguel if you’re interested in Rust+kernel
  - (Nick) [tailcall optimizations for fortified routines](https://reviews.llvm.org/D107872)

## Aug 25, 2021
  - [Error+warning attributes landed](https://reviews.llvm.org/D106030)
  - [30 years of Linux!](https://lwn.net/Articles/867315/)
  - -Wimplicit-fallthrough for 5.15?
    - https://github.com/ClangBuiltLinux/linux/issues/1429
    - https://github.com/llvm/llvm-project/commit/9ed4a94d6451046a51ef393cd62f00710820a7e8
    - https://lore.kernel.org/r/20210819040517.GA329693@embeddedor/
  - ThinLTO regression in LLVM
    - https://github.com/ClangBuiltLinux/linux/issues/1440
    - https://reviews.llvm.org/D106056
    - https://lore.kernel.org/r/5913cdf4-9c8e-38f8-8914-d3b8a3565d73@kernel.org/
  - [CFI x86_64 v2 series](https://lore.kernel.org/r/20210823171318.2801096-1-samitolvanen@google.com)
    - Currently limited to clang-14 but compiler side fix should be going in clang-13.
  - -falign-jumps=0 warning
    - https://lore.kernel.org/r/202108210311.CBtcgoUL-lkp@intel.com/
    - https://lore.kernel.org/r/20210824022640.2170859-1-nathan@kernel.org/
    - https://lore.kernel.org/r/20210824232237.2085342-1-nathan@kernel.org/
  - clang-13 and sanitizer coverage in CI merged
    - https://github.com/ClangBuiltLinux/continuous-integration2/pull/178
    - https://github.com/ClangBuiltLinux/continuous-integration2/pull/179
  - [cc-option-yn removal](https://lore.kernel.org/r/20210817002109.2736222-1-ndesaulniers@google.com/)
  - [-Wbool-operation enhancement](https://reviews.llvm.org/D108003)
  - [PowerPC '-z notext' fix for CONFIG_RELOCATABLE](https://lore.kernel.org/r/20210812204951.1551782-1-morbo@google.com/)
  - [Getting help from Intel on certain bugs](https://groups.google.com/g/clang-built-linux/c/fIy6K5Uxr3s/m/vV--Yt78BgAJ)
  - llvm@lists.linux.dev
    - https://subspace.kernel.org/lists.linux.dev.html
    - https://subspace.kernel.org/#subscribing
  - [LTO kbuild patches](https://lore.kernel.org/lkml/CAK7LNARoxA875uynQHs-HpcfXtzFvuxkzSha9tquR2uV0Za10A@mail.gmail.com/) 
  - Fortify source series for 5.15 then 5.16?
  - Bill looking into zero call registers

## Aug 11, 2021
  - [ARMv4 LLD support discussion `--fix-v4bx`](https://bugs.llvm.org/show_bug.cgi?id=51422) 
  - cc-option-yn necessary?
    - https://groups.google.com/g/clang-built-linux/c/PL9lE_eKhhs 
    - https://github.com/ClangBuiltLinux/linux/issues/1436 
    - https://lore.kernel.org/lkml/20210811175647.3851629-1-ndesaulniers@google.com/ 
    - https://lore.kernel.org/lkml/20210810204240.4008685-1-ndesaulniers@google.com/ 
  - Blog Posts
    - [Funded open source security work at the Linux Foundation](https://linuxfoundation.org/blog/funded-open-source-security-work-at-the-linux-foundation/)
    - [Linux Kernel Security Done Right](https://security.googleblog.com/2021/08/linux-kernel-security-done-right.html) 
  - [Oops! Can’t require LLD for Android R…](https://android-review.googlesource.com/c/platform/test/vts-testcase/kernel/+/1789650/)
  - Death to CROSS_COMPILE
    - https://lore.kernel.org/lkml/20210802183910.1802120-1-ndesaulniers@google.com/ 
    - https://github.com/ClangBuiltLinux/linux/issues/1399 
  - Death to LLVM_IAS=1
    - https://lore.kernel.org/lkml/20210805150102.131008-1-masahiroy@kernel.org/ 
    - https://lore.kernel.org/lkml/20210806172701.3993843-1-ndesaulniers@google.com/ 
    - https://github.com/ClangBuiltLinux/linux/issues/1434 
    - https://github.com/ClangBuiltLinux/continuous-integration2/pull/181 
  - `__attribute__((error(“”))) __attribute__((warning(“”)))` (Nick) for BUILD_BUG and friends
    - https://lore.kernel.org/lkml/20210802202326.1817503-1-ndesaulniers@google.com/ 
    - https://reviews.llvm.org/D107613 
    - https://reviews.llvm.org/D106030 (WIP)
  - [Distro configs now in CI (Fedora, Suse, Arch)](https://github.com/ClangBuiltLinux/continuous-integration2/pull/172) 
  - CFI fix for inline asm references to static functions
    - https://reviews.llvm.org/D104058 
    - https://github.com/ClangBuiltLinux/linux/issues/1354 
  - [LLVM13 CI coverage WIP](https://github.com/ClangBuiltLinux/continuous-integration2/pull/179)
  - [Sanitizer build+boot CI coverage WIP](https://github.com/ClangBuiltLinux/continuous-integration2/pull/178)
  - CFI remove `__typeid__` symbols from JT to aid debugging (Nick)
  - [ASAN ctor/dtor needed to boot test aarch64](https://lore.kernel.org/linux-arch/20210731023107.1932981-1-nathan@kernel.org/)
  - `__builtin_object_size` questions (Kees)
    - How to determine if something is a flexible array member?
      - int foo [0]; // no size, just a marker/symbol that’s addressable
      - int foo []; // flexible array member, malloc + additional size
    - Why can’t flex arrays be in union, or alone in anonymous struct?
      - https://git.kernel.org/pub/scm/linux/kernel/git/kees/linux.git/commit/?h=kspp/memcpy/next-20210803/v2-devel&id=8725f84346c1be20ccb21aedb3e46f25e3ab9f3a 
      - https://git.kernel.org/pub/scm/linux/kernel/git/kees/linux.git/commit/?h=kspp/memcpy/next-20210803/v2-devel&id=0f28d9daf643a1110bc7536f590e60035ba17635 

## July 28, 2021
  - [Fortify Source (Kees)](https://lore.kernel.org/lkml/20210727205855.411487-1-keescook@chromium.org/)
  - [Phoronix benchmarked LTO](https://www.phoronix.com/scan.php?page=article&item=clang-lto-kernel&num=1)
  - Intel 0 day bot now running clang static analyzer continuously
    - https://groups.google.com/g/clang-built-linux/c/NY64cegnl8o 
    - https://groups.google.com/g/clang-built-linux/c/0Kn8V3wI-Jo 
  - RISCV + LTO patches sent
    - https://lore.kernel.org/linux-riscv/20210719205339.1023572-1-twd2.me@gmail.com/ 
    - https://lore.kernel.org/linux-riscv/20210719205247.1023289-1-twd2.me@gmail.com/ 
    - https://lore.kernel.org/linux-riscv/20210719205314.1023455-1-twd2.me@gmail.com/ 
  - [Attr Error + Warning (Nick) WIP](https://reviews.llvm.org/D106030)
    - TODO (Nick): send v3 of CROSS_COMPILE
    - TODO (Nick): Nathan had feedback on one patch `__error__`
  - LLVM14 to branch
  - Max TCWG IRC libaro #linaro-tcwg on libera.chat
  - [Static analysis](https://lore.kernel.org/ksummit/20210723191023.GG25548@kadam/)
  - Sept 21 tentative clang-13 ship

## July 14, 2021
  - [Death to CROSS_COMPILE!](https://lore.kernel.org/lkml/20210708232522.3118208-1-ndesaulniers@google.com/)
  - Death to LLVM_IAS=1
    - [Mips can now be built with LLVM_IAS=1](https://lore.kernel.org/lkml/20210628215029.2722537-1-ndesaulniers@google.com/)
    - Ppc and s390 left
  - ?=
  - RISCV
    - LOCAL
      - https://reviews.llvm.org/D105720 
      - https://sourceware.org/binutils/docs/as/Altmacro.html 
      - https://lore.kernel.org/linux-riscv/CAKwvOdm65wmFQE6_wkVFFE6us99xXoqS8E-qORX9XmsD2uJ1dQ@mail.gmail.com/
    - [VDSO](https://lore.kernel.org/lkml/20210707185105.1180526-1-abdulras@google.com/)
  - (Nick) `__attribute__((error(“”))) __attribute__((warning(“”)))`
  - [ThinLTO inline asm](https://reviews.llvm.org/D104058)
  - [Hexagon allyesconfig almost ready](https://lore.kernel.org/lkml/20210708233849.3140194-1-nathan@kernel.org/)
  - Linaro Connect CFP
  - Rust support? LLVM?
  - [Fallthrough edge case](https://github.com/ClangBuiltLinux/linux/issues/1429)
  - Abigail complex types

## June 30, 2021
  - [PGO on the rocks](https://lore.kernel.org/lkml/CAHk-=whqCT0BeqBQhW8D-YoLLgp_eFY=8Y=9ieREM5xx0ef08w@mail.gmail.com/) 
  - [Should be able to enable LLVM_IAS=1 on mips soon](https://lore.kernel.org/lkml/20210628215029.2722537-1-ndesaulniers@google.com/T/#u)
    - Still some warnings
    - Should we flip LLVM_IAS=1 to on when LLVM=1?
    - PPC
    - S390
  - [Toolchain MC has been accepted at plumbers](https://www.linuxplumbersconf.org/blog/2021/index.php/2021/06/21/toolchains-and-kernel-microconference-accepted-into-2021-linux-plumbers-conference/)
  - More Nest devices switching to clang built kernels
  - Leaving freenode IRC
  - [Send LLVM Revert Checker tool to Tom](https://cs.android.com/android/platform/superproject/+/master:external/toolchain-utils/llvm_tools/revert_checker.py)
  - Fortify source (Kees)
  - -Wrestrict (Kees, Arnd)
  - We can build more 32b ARM? Should we add more to CI?
  - https://tinyurl.com/linux-architectures

## June 16, 2021
  - [RISCV](https://reviews.llvm.org/D103539)
  - [LTO](https://reviews.llvm.org/D104342)
  - [PGO](https://reviews.llvm.org/D104253)
  - [GCOV](https://reviews.llvm.org/D104257) 
  - Bunch of objtool fixes last week (3)
  - https://www.phoronix.com/scan.php?page=news_item&px=Clang-PGO-For-Linux-Next 
  - Working through last minute approvals for plumbers MC
  - Started discussion internally about “hardware for hackers”
  - Distributors conf & CBL meetup 2
  - https://lists.llvm.org/pipermail/llvm-dev/2021-March/149234.html 
  - [#clang-built-linux on LLVM Discord](https://discord.gg/xS7Z362)


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
