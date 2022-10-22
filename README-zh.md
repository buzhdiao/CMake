
# 1. 简要介绍
CMake是一个跨平台、开源的构建系统生成器。

cmake的全部文档都下面两个链接里面：
* cmake Home Page :  https://cmake.org
* cmake Documentation Page:  https://cmake.org/documentation

cmake Comunity Wiki也包含有用的指导和方法。

访问链接是https://gitlab.kitware.com/cmake/community/-/wikis/home


CMake由"Kitware"维护和支持，并和很多社区贡献者合作。

* Kitware : http://www.kitware.com/cmake

# 2. License

CMake is distributed under the OSI-approved BSD 3-clause License.
See `Copyright.txt`for details.

`Copyright.txt`: Copyright.txt

# 3. Building CMake

## 3.1 Supported Platforms

* Microsoft Windows
* Apple macOS
* Linux
* FreeBSD
* OpenBSD
* Solaris
* AIX

其他类似UNIX的操作系统可能是开箱即用的，如果不是的话，将CMake移植到这个平台应该不是一个大问题。
请在论坛上发帖，询问其他人是否有使用该平台的经验。
CMake Discourse Forum: https://discourse.cmake.org

## 3.2 从头开始构建CMake
### 3.2.1 UNIX/Mac OSX/MinGW/MSYS/Cygwin

首先，需要安装C++编译器（支持C++11）和"make"。运行在CMake源目录中找到的"bootstrap"脚本。
可以使用``--help``选项查看支持的选项。
可以使用``--prefix=<install_prefix>``选项为CMake指定自定义安装目录。成功完成后，运行"make"和"make install"。

例如，如果您只想从源代码构建并安装CMake，可以直接在源代码树中构建：
```
  $ ./bootstrap && make && sudo make install
```
或者，如果您计划开发CMake或运行测试套件，请创建单独的构建树：

```
  $ mkdir cmake-build && cd cmake-build
  $ ../cmake-source/bootstrap && make
```

### 3.2.2 Windows

在Windows下构建CMake有两种方法：

1.使用VS 2015或更高版本的MSVC编译。
您需要下载并安装CMake的二进制版本。你可以得到
这些版本来自`CMake Download Page`。然后继续
下面关于`Building CMake with CMake`的说明。

2.在MSYS2下使用MinGW引导。
下载并安装`MSYS2`。然后安装所需的生成工具：
```
$ pacman -S --needed git base-devel mingw-w64-x86_64-gcc
```
和如上所述的引导
* `CMake Download Page`: https://cmake.org/download
* `MSYS2`: https://www.msys2.org/


## 3.3 使用CMake构建CMake

You can build CMake as any other project with a CMake-based build system:
run the installed CMake on the sources of this CMake with your preferred
options and generators. Then build it and install it.
For instructions how to do this, see documentation on `Running CMake`.

你可以使用任何基于CMake的构建系统，将cmake构建为其他工程。基于你的目的选项和生成器，运行源码树中的CMake。接着构建并且安装它。对于具体指导，可以看`Running Cmake`中的文件。

`Running CMake`: https://cmake.org/runningcmake

为了构建指导文件，安装`Sphinx`，并且配置CMake参数`-DSPHINX_HTML=ON`或者`-DSPHINX_MAN=ON` 去使能html或者man构建起。如果这个工具不能自动发现，则添加参数`-DSPHINX_EXECUTABLE=/path/to/sphinx-build`

`Sphinx`: http://sphinx-doc.org

# 4. 报告BUG
如果您发现了错误：
1.如果您有补丁，请阅读“CONTRIBUTING.rst”文档。
2.否则，请在“CMake话语论坛”上发帖询问预期和观察到的行为，以确定它是否真的bug。
3.最后，如果上述步骤无法解决问题，请打开
“CMake Issue Tracker”中的条目。

`CMake Issue Tracker`: https://gitlab.kitware.com/cmake/cmake/-/issues

# 5. 贡献
查看`CONTRIBUTING.rst`去获取贡献说明。
