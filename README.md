# libplutovg.a

From [PlutoVG](https://github.com/sammycage/plutovg) 1.3.3 to /opt/cross-mint/m68k-atari-mint/lib/

Targets: (68000), 68020-060, ColdFire

Uses floating maths and [fdlibm](https://github.com/freemint/fdlibm): 68000 target is without and thus not recommended. 
fdlibm can be downloaded on th-otto [repo](https://tho-otto.m68k.eu/crossmint.php).

## customization

- The malloc/calloc/free functions are replaced by ldg_Malloc/Calloc/Free equivalent to secure stability under MagiC. 
A large amount of Mallocs are made, so it's not safe under monoTOS.

- Export is disabled for all images files format. Work is supposed to be done in memory only.

# installation for makefiles

- /opt/cross-mint/m68k-atari-mint already installed 

- libplutovg.xcodeproj is for Xcode 26.3, you may not need it if you use something else.
