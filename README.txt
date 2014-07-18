OpenVPN GUI 新版简体中文化


-------------------------------

OpenVPN GUI 2.3 版本以及更新版本包含了一个新的 Windows GUI。

但是这个 Windows GUI 没有简体中文的支持，于是自己翻译了一个。


支持简体中文的 OpenVPN GUI 编译方法:

  1.安装 Cygwin -> www.cygwin.com

  2.安装包 make autoconf automake libtool mingw64-i686-*

  3.打下面的补丁

===============================
diff --git a/res/openvpn-gui-res.rc b/res/openvpn-gui-res.rc
index 70b4c82..88a8206 100644
--- a/res/openvpn-gui-res.rc
+++ b/res/openvpn-gui-res.rc
@@ -53,6 +53,7 @@ ID_ICO_DISCONNECTED  ICON  DISCARDABLE  "disconnected.ico"
 #include "openvpn-gui-res-ru.rc"
 #include "openvpn-gui-res-se.rc"
 #include "openvpn-gui-res-tr.rc"
+#include "openvpn-gui-res-zh-CN.rc"
 #include "openvpn-gui-res-zh-hant.rc"
 
 /* Version information and such */

===============================

  4.下载 openvpn-gui-res-zh-CN.rc，放入 OpenVPN GUI git 源代码 res 目录下

  5.编译 openssl

  cd openssl-1.0.1h
  ./Configure --cross-compile-prefix=i686-w64-mingw32- no-zlib mingw
  make
  make install

  6.编译 OpenVPN GUI

  cd openvpn-gui-code
  autoreconf -vif
  ./configure --host=i686-w64-mingw32 OPENSSL_CRYPTO_LIBS="-L/usr/local/ssl/lib/ -lcrypto" OPENSSL_CRYPTO_CFLAGS="-I/usr/local/ssl/include/"
  make

