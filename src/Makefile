CMINI = ../../libcmini/include

CROSSPREFIX=/opt/cross-mint/bin/m68k-atari-mint-
PATH = /opt/cross-mint/m68k-atari-mint/bin:/opt/cross-mint/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
LD_LIBRARY_PATH=/opt/cross-mint/lib:/opt/cross-mint/m68k-atari-mint/lib:$LD_LIBRARY_PATH
DESTDIR=/opt/cross-mint/m68k-atari-mint

CC = $(CROSSPREFIX)gcc
AS = $(CC)
AR = $(CROSSPREFIX)ar
RANLIB = $(CROSSPREFIX)ranlib
STRIP = $(CROSSPREFIX)strip
FLAGS = $(CROSSPREFIX)flags

CFLAGS = -W -I../include -I. -I$(CMINI)

OFLAGS = -Wall -O2 -fomit-frame-pointer -Wno-sign-compare -Wno-unused-function -Wno-unused-parameter \
         -DPLUTOVG_BUILD -DPLUTOVG_BUILD_STATIC \
         -DSTBI_NO_JPEG -DSTBI_NO_PNG -DSTBI_NO_BMP -DSTBI_NO_PSD -DSTBI_NO_TGA -DSTBI_NO_GIF -DSTBI_NO_HDR -DSTBI_NO_PIC -DSTBI_NO_PNM \
         -DPLUTOVG_DISABLE_IMAGE_WRITE -DPLUTOVG_DISABLE_FONT_FACE_CACHE_LOAD

OBJS = plutovg-blend.c \
       plutovg-canvas.c \
       plutovg-font.c \
       plutovg-matrix.c \
       plutovg-paint.c \
       plutovg-path.c \
       plutovg-rasterize.c \
       plutovg-surface.c \
       plutovg-ft-math.c \
       plutovg-ft-raster.c \
       plutovg-ft-stroker.c

libplutovg.a:
	mkdir -p ../lib
	mkdir -p ../lib/m68020-60
	mkdir -p ../lib/m5475

	$(CC) $(CFLAGS) -m68000 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libplutovg.a $(DESTDIR)/lib/libplutovg.a
	cp libplutovg.a ../lib/libplutovg.a
	rm -f *.o libplutovg.a
	$(CC) $(CFLAGS) -m68020-60 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libplutovg.a $(DESTDIR)/lib/m68020-60/libplutovg.a
	cp libplutovg.a ../lib/m68020-60/libplutovg.a
	rm -f *.o libplutovg.a
	$(CC) $(CFLAGS) -mcpu=5475 $(OFLAGS) -c $(OBJS)
	$(AR) -rcs $@ *.o
	$(AR) s $@
	cp libplutovg.a $(DESTDIR)/lib/m5475/libplutovg.a
	cp libplutovg.a ../lib/m5475/libplutovg.a
	rm -f *.o libplutovg.a

clean:
	rm -f ../lib/libplutovg.a
	rm -f ../lib/m68020-60/libplutovg.a
	rm -f ../lib/m5475/libplutovg.a
	rm -f *.o libplutovg.a
