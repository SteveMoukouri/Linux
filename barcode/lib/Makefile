DESTDIR = /usr/local
SRCFILES = codabar.c code11.c code128.c code39.c code93.c ean.c i25.c library.c msi.c pcl.c plessey.c ps.c svg.c
OBJ = $(SRCFILES:.c=.o)
CC = gcc
CPPFLAGS = -DHAVE_CONFIG_H -I. -DHAVE_CONFIG_H -DNO_LIBPAPER
CFLAGS = -g -O2
AR = ar
ARFLAGS = cr
RANLIB = ranlib

all: libbarcode.a

libbarcode.a: $(OBJ)
	$(AR) $(ARFLAGS) $@ $(OBJ)
	$(RANLIB) $@

%.o: %.c
	$(CC) -c $(CPPFLAGS) $(CFLAGS) $< -o $@

install:
	mkdir -p $(DESTDIR)/lib && cp libbarcode.a $(DESTDIR)/lib
	mkdir -p $(DESTDIR)/include && cp barcode.h $(DESTDIR)/include

uninstall:
	rm -f $(DESTDIR)/include/barcode.h  $(DESTDIR)/lib/libbarcode.a

clean:
	rm -f $(OBJ) libbarcode.a

.PHONY: all clean install uninstall
