DESTDIR = /usr/local
CC = gcc
CFLAGS = -g -O2
SRCFILES = cmdline.c main.c sample.c
OBJ = $(SRCFILES:.c=.o)
CPPFLAGS = -DHAVE_CONFIG_H -DNO_LIBPAPER -I. -I.. -I../lib
LDFLAGS = -L../lib
LDLIBS = -lbarcode

all: barcode sample

test: barcode bonjour.test
#	@./barcode -b test-bonjour -E > test-bonjour.eps
#	@cmp bonjour.eps test-bonjour.eps
	@./barcode -b bonjour -E > bonjour.eps
	@cmp bonjour.test bonjour.eps

barcode: $(OBJ) ../lib/libbarcode.a
	$(CC) -o $@ cmdline.o main.o $(LDFLAGS) $(LDLIBS)

sample: sample.o  ../lib/libbarcode.a
	$(CC) -o $@ sample.o $(LDFLAGS) $(LDLIBS)

%.o: %.c
	$(CC) -c $(CPPFLAGS) $(CFLAGS) $< -o $@

../lib/libbarcode.a:
	cd ../lib; $(MAKE)

install:
	mkdir -p $(DESTDIR)/bin && cp barcode $(DESTDIR)/bin

uninstall:
	rm -f $(DESTDIR)/bin/barcode

clean:
	rm -f $(OBJ) sample barcode test-bonjour.eps bonjour.eps

.PHONY: all clean test install uninstall
