OpenVPN GUI 新版简体中文化

-------------------------------

官方源代码没有简体中文的翻译，于是自己翻了一个。


编译方法:

  1.安装Cygwin -> www.cygwin.com

  2.安装包 make autoconf automake libtool mingw64-i686-*

  3.打下面的补丁

===============================
--- res/openvpn-gui-res-orig.rc	2014-07-08 01:47:32 +0100
+++ res/openvpn-gui-res.rc	2014-07-07 01:21:06 +0100
@@ -53,6 +53,7 @@
 #include "openvpn-gui-res-ru.rc"
 #include "openvpn-gui-res-se.rc"
 #include "openvpn-gui-res-tr.rc"
+#include "openvpn-gui-res-zh-CN.rc"
 #include "openvpn-gui-res-zh-hant.rc"
 
 /* Version information and such */

===============================

  4.编译 openssl

  cd openssl-1.0.1h
  ./Configure --cross-compile-prefix=i686-w64-mingw32- no-zlib mingw
  make
  make install

  5.编译 OpenVPN GUI

  cd openvpn-gui-code
  autoreconf -vif
  ./configure --host=i686-w64-mingw32 OPENSSL_CRYPTO_LIBS="-L/usr/local/ssl/lib/ -lcrypto" OPENSSL_CRYPTO_CFLAGS="-I/usr/local/ssl/include/"
  make

