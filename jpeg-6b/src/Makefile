CC = gcc
LIB_SRC = jcapimin.c jcapistd.c jccoefct.c jccolor.c jcdctmgr.c jchuff.c jcinit.c jcmainct.c jcmarker.c jcmaster.c jcomapi.c jcparam.c jcphuff.c jcprepct.c jcsample.c jctrans.c jdapimin.c jdapistd.c jdatadst.c jdatasrc.c jdcoefct.c jdcolor.c jddctmgr.c jdhuff.c jdinput.c jdmainct.c jdmarker.c jdmaster.c jdmerge.c jdphuff.c jdpostct.c jdsample.c jdtrans.c jerror.c jfdctflt.c jfdctfst.c jfdctint.c jidctflt.c jidctfst.c jidctint.c jidctred.c jquant1.c jquant2.c jutils.c jmemmgr.c jmemnobs.c
LIB_OBJ = $(LIB_SRC:.c=.o)
AR = ar
ARFLAGS = cru
RANLIB = ranlib
CFLAG = -O2 -Wall -ansi -pedantic
CPPFLAGS = -I..
CJPEG_SRC = cjpeg.c rdppm.c rdgif.c rdtarga.c rdrle.c rdbmp.c rdswitch.c cdjpeg.c
CJPEG_OBJ = $(CJPEG_SRC:.c=.o)
DJPEG_SRC = djpeg.c wrppm.c wrgif.c wrtarga.c wrrle.c wrbmp.c rdcolmap.c cdjpeg.c
DJPEG_OBJ = $(DJPEG_SRC:.c=.o)
JPEGTRAN_SRC = jpegtran.c rdswitch.c cdjpeg.c transupp.c
JPEGTRAN_OBJ = $(JPEGTRAN_SRC:.c=.o)
DESTDIR = /usr/local 

all: depend libjpeg.a cjpeg djpeg jpegtran wrjpgcom rdjpgcom install

depend:
	$(CC) -MM $(CPPFLAGS) $(LIB_SRC) $(CJPEG_SRC) $(DJPEG_SRC) $(JPEGTRAN_SRC) > .depend
-include .depend

jcapimin.c jcapistd.c jccoefct.c jccolor.c jcdctmgr.c jchuff.c jcinit.c jcmainct.c jcmarker.c jcmaster.c jcomapi.c jcparam.c jcphuff.c jcprepct.c jcsample.c jctrans.c jdapimin.c jdapistd.c jdatadst.c jdatasrc.c jdcoefct.c jdcolor.c jddctmgr.c jdhuff.c jdinput.c jdmainct.c jdmarker.c jdmaster.c jdmerge.c jdphuff.c jdpostct.c jdsample.c jdtrans.c jerror.c jfdctflt.c jfdctfst.c jfdctint.c jidctflt.c jidctfst.c jidctint.c jidctred.c jquant1.c jquant2.c jutils.c jmemmgr.c jmemnobs.c: jconfig.h

cjpeg: $(CJPEG_OBJ) libjpeg.a
	$(CC) $(CJPEG_OBJ) libjpeg.a -o $@ $(CFLAG) $(CPPFLAGS)

djpeg: $(DJPEG_OBJ) libjpeg.a
	$(CC) $(DJPEG_OBJ) libjpeg.a -o $@ $(CFLAG) $(CPPFLAGS)

jpegtran: $(JPEGTRAN_OBJ) libjpeg.a
	$(CC) $(JPEGTRAN_OBJ) libjpeg.a -o $@ $(CFLAG) $(CPPFLAGS)

rdjpgcom: rdjpgcom.c
	$(CC)  rdjpgcom.c -o $@ $(CFLAG) $(CPPFLAGS)

wrjpgcom: wrjpgcom.c
	$(CC)  wrjpgcom.c -o $@ $(CFLAG) $(CPPFLAGS)

jconfig.h: ckconfig.c
	$(CC) ckconfig.c -o ckconfig $(CFLAG) $(CPPFLAGS)
	./ckconfig

%.o: %.c
	$(CC) -c $(CFLAGS) $(CPPFLAGS) $< -o $@

libjpeg.a: jconfig.h $(LIB_OBJ)
	$(AR) $(ARFLAGS) $@ $(LIB_OBJ)
	$(RANLIB) $@        

install: libjpeg.a jconfig.h jpeglib.h jerror.h jpegint.h cjpeg djpeg jpegtran rdjpgcom wrjpgcom
	mkdir -p $(DESTDIR)/lib
	cp libjpeg.a $(DESTDIR)/lib
	mkdir -p $(DESTDIR)/include
	cp jconfig.h jpeglib.h jerror.h jpegint.h $(DESTDIR)/include
	mkdir -p $(DESTDIR)/bin
	cp cjpeg djpeg jpegtran rdjpgcom wrjpgcom $(DESTDIR)/bin

clean:
	rm -f $(LIB_OBJ) $(CJPEG_OBJ) $(DJPEG_OBJ) $(JPEGTRAN_OBJ) wrjpgcom rdjpgcom jpegtran djpeg cjpeg libjpeg.a .depend ckconfig jconfig.h

.PHONY: all depend clean
