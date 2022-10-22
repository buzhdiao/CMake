以下是针对开发人员的CMake源代码指南。
有关详细信息，请参阅“CMake Development”文档。

* `CMake Development`: README.rst

C++ 代码风格
==============

We use `clang-format` version **6.0** to define our style for C++ code in
the CMake source tree.  See the `.clang-format` configuration file for our
style settings.  Use the `Utilities/Scripts/clang-format.bash` script to
format source code.  It automatically runs ``clang-format`` on the set of
source files for which we enforce style.  The script also has options to
format only a subset of files, such as those that are locally modified.

* `clang-format`: http://clang.llvm.org/docs/ClangFormat.html
* `.clang-format`: ../../.clang-format
* `Utilities/Scripts/clang-format.bash`: ../../Utilities/Scripts/clang-format.bash

允许的C++子集
====================

CMake requires compiling as C++11 in order to support building on older
toolchains.  However, to facilitate development, some standard library
features from more recent C++ standards are supported through a compatibility
layer.  These features are defined under the namespace ``cm`` and headers
are accessible under the ``cm/`` directory.  The headers under ``cm/`` can
be used in place of the standard ones when extended features are needed.
For example ``<cm/memory>`` can be used in place of ``<memory>``.

Available features are:

* From ``C++14``:

  * ``<cm/array>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/deque>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/forward_list>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/iomanip>``:
    ``cm::quoted``

  * ``<cm/iterator>``:
    ``cm::make_reverse_iterator``, ``cm::cbegin``, ``cm::cend``,
    ``cm::rbegin``, ``cm::rend``, ``cm::crbegin``, ``cm::crend``

  * ``<cm/list>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/map>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/memory>``:
    ``cm::make_unique``

  * ``<cm/set>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/string>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/string_view>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/shared_mutex>``:
    ``cm::shared_lock``

  * ``<cm/type_traits>``:
    ``cm::enable_if_t``

  * ``<cm/unordered_map>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/unordered_set>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

  * ``<cm/vector>``:
    ``cm::cbegin``, ``cm::cend``, ``cm::rbegin``, ``cm::rend``,
    ``cm::crbegin``, ``cm::crend``

* From ``C++17``:

  * ``<cm/algorithm>``:
    ``cm::clamp``

  * ``<cm/array>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/deque>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``cm/filesystem>``:
    ``cm::filesystem::path``

  * ``<cm/forward_list>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/iterator>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/list>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/map>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/optional>``:
    ``cm::nullopt_t``, ``cm::nullopt``, ``cm::optional``,
    ``cm::make_optional``, ``cm::bad_optional_access``

  * ``<cm/set>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/shared_mutex>``:
    ``cm::shared_mutex``

  * ``<cm/string>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/string_view>``:
    ``cm::string_view``, ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/type_traits>``:
    ``cm::bool_constant``, ``cm::invoke_result_t``, ``cm::invoke_result``,
    ``cm::void_t``

  * ``<cm/unordered_map>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/unordered_set>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

  * ``<cm/utility>``:
    ``cm::in_place_t``, ``cm::in_place``

  * ``<cm/vector>``:
    ``cm::size``, ``cm::empty``, ``cm::data``

* From ``C++20``:

  * ``<cm/array>``:
    ``cm::ssize``

  * ``<cm/deque>``:
    ``cm::erase``, ``cm::erase_if``, ``cm::ssize``

  * ``<cm/forward_list>``:
    ``cm::ssize``

  * ``<cm/iterator>``:
    ``cm::ssize``

  * ``<cm/list>``:
    ``cm::erase``, ``cm::erase_if``, ``cm::ssize``

  * ``<cm/map>`` :
    ``cm::erase_if``, ``cm::ssize``

  * ``<cm/set>`` :
    ``cm::erase_if``, ``cm::ssize``

  * ``<cm/string_view>``:
    ``cm::ssize``

  * ``<cm/string>``:
    ``cm::erase``, ``cm::erase_if``, ``cm::ssize``

  * ``<cm/unordered_map>``:
    ``cm::erase_if``, ``cm::ssize``

  * ``<cm/unordered_set>``:
    ``cm::erase_if``, ``cm::ssize``

  * ``<cm/vector>``:
    ``cm::erase``, ``cm::erase_if``, ``cm::ssize``

Additionally, some useful non-standard extensions to the C++ standard library
are available in headers under the directory ``cmext/`` in namespace ``cm``.
These are:

* ``<cmext/algorithm>``:

  * ``cm::append``:
    Append elements to a sequential container.

  * ``cm::contains``:
    Checks if element or key is contained in container.

* ``<cmext/enum_set>``

  * ``cm::enum_set``:
    Container to manage set of elements from an ``enum class`` definition.

* ``<cmext/iterator>``:

  * ``cm::is_terator``:
    Checks if a type is an iterator type.

  * ``cm::is_input_iterator``:
    Checks if a type is an input iterator type.

  * ``cm::is_range``:
    Checks if a type is a range type: functions ``std::begin()`` and
    ``std::end()`` apply.

  * ``cm::is_input_range``:
    Checks if a type is an input range type: functions ``std::begin()`` and
    ``std::end()`` apply and return an input iterator.

* ``<cmext/memory>``:

  * ``cm::static_reference_cast``:
    Apply a ``static_cast`` to a smart pointer.

  * ``cm::dynamic_reference_cast``:
    Apply a ``dynamic_cast`` to a smart pointer.

* ``<cmext/type_traits>``:

  * ``cm::is_container``:
    Checks if a type is a container type.

  * ``cm::is_associative_container``:
    Checks if a type is an associative container type.

  * ``cm::is_unordered_associative_container``:
    Checks if a type is an unordered associative container type.

  * ``cm::is_sequence_container``:
    Checks if a type is a sequence container type.

  * ``cm::is_unique_ptr``:
    Checks if a type is a ``std::unique_ptr`` type.

CMake assumes the compiler supports ``#pragma once``. Use this for all
hand-written header files.

动态内存管理
=========================

To ensure efficient memory management, i.e. no memory leaks, it is required
to use smart pointers.  Any dynamic memory allocation must be handled by a
smart pointer such as ``std::unique_ptr`` or ``std::shared_ptr``.

It is allowed to pass raw pointers between objects to enable objects sharing.
A raw pointer **must** not be deleted. Only the object(s) owning the smart
pointer are allowed to delete dynamically allocated memory.

第三方库
=============

To build CMake, some third parties are needed. Under ``Utilities``
directory, are versions of these third parties which can be used as an
alternate to the ones provided by the system.

To enable the selection of the third parties between the system and CMake ones,
in CMake sources, third parties headers must be prefixed by ``cm3p/``
(for example: ``<cm3p/json/reader.h>``). These wrappers are located under
``Utilities/cm3p`` directory.

源码树布局
==================

CMake源代码树的组织如下。

* ``Auxiliary/``:
  Shell和编辑器集成文件。
* ``Help/``:
  Documentation.  See the `CMake Documentation Guide`.
  * ``Help/dev/``: 开发人员文档。
    
  * ``Help/release/dev/``: 发布自上次发布以来用于开发的注释片段。
* ``Licenses/``: 二进制发行版中第三方库的许可文件。
* ``Modules/``: CMake语言模块随CMake一起安装。
* ``Packaging/``: 用于打包CMake自身以供分发的文件。
* ``Source/``:  CMake本身的源代码。
* ``Templates/``:  和cmake一起分发的文件，比如生成器，打包器等。
* ``Tests/``: 测试套， 查看`Tests/README.rst`.
* ``Utilities/``:  脚本，第三方源代码。
  * ``Utilities/std/cm``:
    Support files for various C++ standards.
  
  * ``Utilities/std/cmext``:
    Extensions to the C++ STL.
  
  * ``Utilities/cm3p``:
    Public headers for third parties needed to build CMake.
  
  * ``Utilities/Sphinx/``:
    Sphinx configuration to build CMake user documentation.
  
  * ``Utilities/Release/``:
    Scripts used to package CMake itself for distribution on ``cmake.org``.
    See `Utilities/Release/README.rst`.
* `CMake Documentation Guide`: documentation.rst
* `Tests/README.rst`: ../../Tests/README.rst
* `Utilities/Release/README.rst`: ../../Utilities/Release/README.rst
