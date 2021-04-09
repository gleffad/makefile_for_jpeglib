DESTDIR = /usr/local 

all:
	cd src && $(MAKE) -r all 
	cd tests && $(MAKE) -r check

install:
	cd src && $(MAKE) -r install DESTDIR=$(DESTDIR)
	mkdir -p $(DESTDIR)/share/man/man1
	cp man/*.1 $(DESTDIR)/share/man/man1
	mkdir -p $(DESTDIR)/share/doc/jpeg-6b
	gzip doc/*.doc
	cp doc/*.gz $(DESTDIR)/share/doc/jpeg-6b
	gunzip doc/*
	mkdir -p $(DESTDIR)/share/jpeg-6b
	cp README change.log $(DESTDIR)/share/jpeg-6b

clean:
	cd src && $(MAKE) -r clean
	cd tests && $(MAKE) -r clean

.PHONY: all install clean
