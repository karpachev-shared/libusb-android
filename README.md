# libusb

libusb is a library for USB device access from Linux, macOS,
Windows, OpenBSD/NetBSD, Haiku, Solaris userspace, and WebAssembly
via WebUSB.
It is written in C (Haiku backend in C++) and licensed under the GNU
Lesser General Public License version 2.1 or, at your option, any later
version (see [COPYING](COPYING)).

libusb is abstracted internally in such a way that it can hopefully
be ported to other operating systems. Please see the [PORTING](PORTING)
file for more information.

libusb homepage:
http://libusb.info/

Developers will wish to consult the API documentation:
http://api.libusb.info

Use the mailing list for questions, comments, etc:
http://mailing-list.libusb.info

- Hans de Goede <hdegoede@redhat.com>
- Xiaofan Chen <xiaofanc@gmail.com>
- Ludovic Rousseau <ludovic.rousseau@gmail.com>
- Nathan Hjelm <hjelmn@cs.unm.edu>
- Chris Dickens <christopher.a.dickens@gmail.com>

(Please use the mailing list rather than mailing developers directly)

# Подготовка проекта к сборке

Для сборки проекта под андроид необходимо добавить и настроить toolchain. Для
этого переходим в "Settings -> Build, Execution, Deployment -> Toolchains" и
добавляем новый toolchain типа System. Переименовываем toolchain при желании.
Затем нажимаем на "Add environment" и добавляем путь к файлу окружения.
Содержимое файла окружения должно быть таким (user-home-dir заменить на путь до домашнего каталога):
```shell
export NDK=user-home-dir/Library/Android/sdk/ndk/23.1.7779620
export TOOLCHAIN=$NDK/toolchains/llvm/prebuilt/darwin-x86_64
export TARGET=aarch64-linux-android
export API=24
export AR=$TOOLCHAIN/bin/llvm-ar
export CC=$TOOLCHAIN/bin/$TARGET$API-clang
export AS=$CC
export CXX=$TOOLCHAIN/bin/$TARGET$API-clang++
export LD=$TOOLCHAIN/bin/ld
export RANLIB=$TOOLCHAIN/bin/llvm-ranlib
export STRIP=$TOOLCHAIN/bin/llvm-strip
```