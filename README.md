[![license](https://img.shields.io/github/license/micro-os-plus/platform-sifive-arty-xpack)](https://github.com/micro-os-plus/platform-sifive-arty-xpack/blob/xpack/LICENSE)
[![CI on Push](https://github.com/micro-os-plus/platform-sifive-arty-xpack/workflows/CI%20on%20Push/badge.svg)](https://github.com/micro-os-plus/platform-sifive-arty-xpack/actions?query=workflow%3A%22CI+on+Push%22)

# A source xPack with the µOS++ SiFive Core Complex IP Arty boards specific files

This project provides support for the SiFive synthesised E31/E51 devices
running on the Arty development board.

The project is hosted on GitHub as
[micro-os-plus/platform-sifive-arty-xpack](https://github.com/micro-os-plus/platform-sifive-arty-xpack).

## Maintainer info

This page is addressed to developers who plan to include this package
into their own projects.

For maintainer infos, please see the
[README-MAINTAINER](README-MAINTAINER.md) file.

### Prerequisites

A recent [`xpm`](https://www.npmjs.com/package/xpm), which is a
portable [Node.js](https://nodejs.org/) command line application.

Compiling the source code requires a modern C++ compiler, preferably
GCC 5 or higher. 

## Install

As a source xPacks, the easiest way to add it to a project is via **xpm**,
but it can also be used as any Git project, for example as a submodule.

### Prerequisites

A recent [xpm](https://xpack.github.io/xpm/),
which is a portable [Node.js](https://nodejs.org/) command line application.

For details please follow the instructions in the
[install](https://xpack.github.io/install/) page.

### xpm

Note: the package will be available from npmjs.com at a later date.

For now, it can be installed from GitHub:

```console
$ cd <project>
$ xpm init # Unless a package.json is already present

$ xpm install github:micro-os-plus/platform-sifive-arty-xpack
```

When ready, this package will be available as
[`@xpack-sifive/platform-arty`](https://www.npmjs.com/package/@xpack-sifive/platform-arty)
from the `npmjs.com` registry:

```console
$ cd <project>
$ xpm init # Unless a package.json is already present

$ xpm install @xpack-sifive/platform-arty@latest
```

### Git submodule

If, for any reason, **xpm** is not available, the next recommended
solution is to link it as a Git submodule below an `xpacks` folder.

```console
$ cd <project>
$ git init # Unless already a Git project
$ mkdir -p xpacks

$ git submodule add https://github.com/micro-os-plus/platform-sifive-arty-xpack.git \
  xpacks/micro-os-plus-platform-sifive-arty
```

## Branches

Apart from the unused `master` branch, there are two active branches:

- `xpack`, with the latest stable version
- `xpack-develop`, with the current development version

All development is done in the `xpack-develop` branch, and contributions via
Pull Requests should be directed to this branch.

When new releases are published, the `xpack-develop` branch is merged
into `xpack`.

## User info

TBD

### Status

The SiFive Arty definitions are fully functional.

### Build & integration info

To include this package in a project, consider the following details.

#### Source folders

- `src`

#### Include folders

- `include`

The standard way to include the board files is

```c
#include <micro-os-plus/platform.h>
```

#### Preprocessor definitions

- `SIFIVE_E31ARTY_BOARD`
- `SIFIVE_E51ARTY_BOARD`

#### Compiler options

- `-std=c++17` or higher for C++ sources
- `-std=c11` for C sources

#### Namespaces

TBD

#### Classes

TBD

#### E31/E51 Core Complex FPGA Eval Kit Clock and Reset

The E31/E51 Core Complex FPGA Eval Kit has a 100MHz input to the
FPGA. This is used to derive the Core Complex’s `io_coreClock` at
65 MHz, and the clock (peripheral clock) at 32.5 MHz. The
`io_rtcToggle` is driven at approximately 32kHz.

The system reset driven by the Reset Button on the evaluation board
is combined with the external debugger’s `SRST_n` pin as a full
system reset for the E31/E51 Core Complex FPGA Eval KitT ̇his is
combined with the `io_ndreset` to drive the reset input to the Core Complex.

The reset vector is set with Switch 0. Leave the switch in the
“Off” position to execute from SPI Flash.

#### Global interrupts

- UART TX/RX	1
- SWITCH 0 2
- SWITCH 1 3
- SWITCH 2 4
- SWITCH 3 5
- Quad SPI 6
- GPIO[0] LED 0 RED 	7
- GPIO[1] LED 0 GREEN	8
- GPIO[2] LED 0 BLUE	9
- GPIO[3] SWITCH 3	10
- GPIO[4] BUTTON 0	11
- GPIO[5] BUTTON 1	12
- GPIO[6] BUTTON 2	13
- GPIO[7] BUTTON 3	14
- GPIO[8] PMOD A[0]	15
- GPIO[9] PMOD A[1]	16
- GPIO[10] PMOD A[2]	17
- GPIO[11] PMOD A[3]	18
- GPIO[12] PMOD A[4]	19
- GPIO[13] PMOD A[5]	20
- GPIO[14] PMOD A[6]	21
- GPIO[15] PMOD A[7]	22
- PWM CMP[0] 23
- PWM CMP[1] LED 1 RED 24
- PWM CMP[2] LED 1 GREEN 25
- PWM CMP[3] LED 1 BLUE 26

### Examples

TBD

### Known problems

- none

### Tests

TBD

## License

The original content is released under the
[MIT License](https://opensource.org/licenses/MIT/),
with all rights reserved to
[Liviu Ionescu](https://github.com/ilg-ul/).
