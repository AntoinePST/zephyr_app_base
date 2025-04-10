**Application base**

In the folder where you create your application, you will have files that connect your application with the Zephyr OS and any extra modules you need. This folder will have all the files specific to your application, such as configuration settings and the actual code you write.

Here is a typical structure of a basic Zephyr application:
```
<app>                  // Application folder
   ├── build/          // appears once you have built your app
   |    ├── […]
   |
   ├── src/
   |    └── main.c
   |
   ├── app.overlay
   ├── CMakeLists.txt
   ├── prj.conf
   └── VERSION

```

##### build/
This folder appears once you have built your application and contains the files used to flash your microcontroller. Some interesting files in this directory include:

`build/zephyr/zephyr.dts`: CMake uses a devicetree to tailor the build for your specific architecture/board. This is the final version of that file, where you can find all the different functionalities (GPIO, Timers, PWM, DMA, UART, SPI, I2C, DAC, USB, etc.) present on your MCU, which can then be used in your application.

`build/zephyr/.config`: The final Kconfig used for your build. This can be useful to verify if a setting has been set correctly.

`build/zephyr/zephyr.elf`: This is the final executable binary, containing the compiled code of your application and all its dependencies, used for flashing the target microcontroller or for debugging.

##### src/main.c
This is a source code file. Applications typically contain source files written in C, C++, or assembly language. According to Zephyr conventions, these files should be placed in a subdirectory named `src` within your application directory.

##### CMakeLists.txt
This file instructs the build system on where to find the other application files and links the application directory with Zephyr’s CMake build system. This linkage provides features supported by Zephyr’s build system, such as board-specific configuration files, the ability to run and debug compiled binaries on real or emulated hardware, and more.

##### VERSION
A text file that contains several version information fields. These fields let you manage the lifecycle of the application and automate providing the application version when signing application images.

See [Application version management](https://docs.zephyrproject.org/latest/build/version/index.html#app-version-details) for more information about this file and how to use it.

##### app.overlay
This is a devicetree overlay file that specifies application-specific changes which should be applied to the base devicetree for any board you build for. The purpose of devicetree overlays is usually to configure something about the hardware used by the application.

The build system looks for `app.overlay` by default, but you can add more devicetree overlays, and other default files are also searched for.

See [Devicetree](https://docs.zephyrproject.org/latest/build/dts/index.html#devicetree) for more information about devicetree.

##### prj.conf
This is a Kconfig fragment specifying application-specific values for one or more Kconfig options. These settings are merged with other settings to produce the final configuration. Kconfig fragments are usually used to configure software features for the application.

The build system looks for `prj.conf` by default, but you can add more Kconfig fragments and other default files.

See [Kconfig](https://docs.zephyrproject.org/latest/develop/application/index.html#application-kconfig) Configuration below for more information.
