---
title: Tree Sitter
description: Some page
layout: "@layouts/MainLayout.astro"
---


## <a id="Nvim" class="section-title" href="#Nvim"> Support Txt</a> 

NVIM REFERENCE MANUAL


Support

Type [gO](#gO) to see the table of contents.


## <a id="supported-platforms" class="section-title" href="#supported-platforms">Supported Platforms</a> 

`System`          `Tier`      `Versions`                  `Tested versions`
Linux            1      >= 2.6.32, glibc >= 2.12     Ubuntu 20.04
macOS (Intel)    1      >= 10.15                     macOS 11
Windows 64-bit   1      >= 8                         Windows Server 2019
FreeBSD          1      >= 10                        FreeBSD 13
macOS (M1)       2      >= 10.15
OpenBSD          2      >= 7
MinGW            2      MinGW-w64

Support types ~

* Tier 1: Officially supported and tested with CI. Any contributed patch
MUST NOT break such systems.

* Tier 2: Officially supported, but not necessarily tested with CI. These
systems are maintained to the best of our ability, without being a top
priority.

* Tier 3: Not tested and no guarantees, but may work.

Adding support for a new platform ~

IMPORTANT: Before attempting to add support for a new platform please open
an issue about it for discussion.


## <a id="" class="section-title" href="#">Common</a> 

Some common notes when adding support for new platforms:

Cmake is the only supported build system. The platform must be buildable with cmake.

All functionality related to the new platform must be implemented in its own
file inside `src/nvim/os` unless it's already done in a common file, in which
case adding an `#ifdef` is fine.


vim:tw=78:ts=8:et:ft=help:norl:

