DESTDIR = /usr/local

all:
	cd src; $(MAKE) $@
	cd lib; $(MAKE) $@

test:
	@cd src; $(MAKE) $@

clean:
	cd src; $(MAKE) $@
	cd lib; $(MAKE) $@
	cd doc; rm -f barcode.1.gz barcode.3.gz barcode.info

install:
	cd src; $(MAKE) install DESTDIR=$(DESTDIR)
	cd lib; $(MAKE) install DESTDIR=$(DESTDIR)
	cd doc; gzip -c barcode.1 > barcode.1.gz
	cd doc; gzip -c barcode.3 > barcode.3.gz
	mkdir -p $(DESTDIR)/share/barcode $(DESTDIR)/share/man/man1 $(DESTDIR)/share/man/man3 $(DESTDIR)/share/info
	cp doc/barcode.1.gz $(DESTDIR)/share/man/man1
	cp doc/barcode.3.gz $(DESTDIR)/share/man/man3
	cd doc; makeinfo barcode.texi
	cp doc/barcode.info $(DESTDIR)/share/info
	cp AUTHORS COPYING ChangeLog NEWS TODO README $(DESTDIR)/share/barcode

uninstall:
	cd src; $(MAKE) uninstall DESTDIR=$(DESTDIR)
	cd lib; $(MAKE) uninstall DESTDIR=$(DESTDIR)
	rm -f  $(DESTDIR)/share/barcode/* $(DESTDIR)/share/info/* $(DESTDIR)/share/man/man3/* $(DESTDIR)/share/man/man1/*

.PHONY: clean test all uninstall install
