**Application base**

## src/main.c
A source code file. Applications typically contain source files written in C, C++, or assembly language. The Zephyr convention is to place them in a subdirectory of `<app>` named `src`.

## CMakeLists.txt
This file tells the build system where to find the other application files, and links the application directory with Zephyr’s CMake build system. This link provides features supported by Zephyr’s build system, such as board-specific configuration files, the ability to run and debug compiled binaries on real or emulated hardware, and more.

## VERSION
A text file that contains several version information fields. These fields let you manage the lifecycle of the application and automate providing the application version when signing application images.

See [Application version management](https://docs.zephyrproject.org/latest/build/version/index.html#app-version-details) for more information about this file and how to use it.

## app.overlay
This is a devicetree overlay file that specifies application-specific changes which should be applied to the base devicetree for any board you build for. The purpose of devicetree overlays is usually to configure something about the hardware used by the application.

The build system looks for `app.overlay` by default, but you can add more devicetree overlays, and other default files are also searched for.

See [Devicetree](https://docs.zephyrproject.org/latest/build/dts/index.html#devicetree) for more information about devicetree.

## prj.conf
This is a Kconfig fragment that specifies application-specific values for one or more Kconfig options. These application settings are merged with other settings to produce the final configuration. The purpose of Kconfig fragments is usually to configure the software features used by the application.

The build system looks for `prj.conf` by default, but you can add more Kconfig fragments, and other default files are also searched for.

See [Kconfig](https://docs.zephyrproject.org/latest/develop/application/index.html#application-kconfig) Configuration below for more information.
