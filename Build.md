Some of these steps could be unnecessary. However, this worked and I don't care :)

Install these:
* [Win32OpenSSL-1_0_2r.exe](https://slproweb.com/download/Win32OpenSSL-1_0_2r.exe) 				=>	 C:\OpenSSL-Win32
* [mingw-w32-bin_i686-mingw_20111031_sezero](https://master.dl.sourceforge.net/project/mingw-w64/Toolchains%20targetting%20Win64/Personal%20Builds/sezero_4.4_20111031/mingw-w64-bin_i686-mingw_20111031_sezero.zip)  	=>   C:\mingw32.4.4 (colud be C:\mingw32, but I have other versions)
* [qt-win-opensource-4.7.4-mingw.exe](http://mirrors-wan.geekpie.club/qtproject/archive/qt/4.7/qt-win-opensource-4.7.4-mingw.exe)  	=>   c:\QT\4.7.4\
* qt-creator-opensource-windows-x86_64-4.8.1.exe (optional)

Add theses to  c:\QT\4.7.4\src\src.pro
```
win32:QMAKE_LFLAGS += -openssl-linked
OPENSSL_LIBS = -LC:/OpenSSL-Win32/lib/MinGW/ -lssleay32 -llibeay32

INCLUDEPATH += C:/OpenSSL-Win32/include
LIBS += -LC:/OpenSSL-Win32/lib/MinGW/ -llibeay32 -lssleay32
```



Add these tp c:\QT\4.7.4\src\network\network.pro
```
#win32:QMAKE_LFLAGS += -shared
win32:QMAKE_LFLAGS += -openssl-linked
OPENSSL_LIBS = -LC:/OpenSSL-Win32/lib/MinGW/ -lssleay32 -llibeay32

INCLUDEPATH += C:/OpenSSL-Win32/include
LIBS += -LC:/OpenSSL-Win32/lib/MinGW/ -llibeay32 -lssleay32
```


C:\Qt\4.7.4>set PATH=%PATH%;C:\mingw32.4.4\bin\


C:\Qt\4.7.4>mingw32-make --version
```
GNU Make 3.82
Built for i686-w64-mingw32
Copyright (C) 2010  Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

C:\Qt\4.7.4>qmake --version
```
Qt: Untested Windows version 6.2 detected!
QMake version 2.01a
Using Qt version 4.7.4 in C:/Qt/4.7.4/lib
```

C:\Qt\4.7.4>configure.exe  -openssl -openssl-linked


C:\Qt\4.7.4>mingw32-make
