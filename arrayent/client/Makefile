#
# Copyright (C) 2010-, Marvell International Ltd.
# All Rights Reserved
#
#
# File: application Makefile
#
# Purpose: This is a toplevel makefile for compiling the
#        applications and utilities in subfolders
#

include ./config

BINDIR  = ./bin

PRGNAME = aicclient
#PRG2NAME = aicrxclient

OBJS	:= client.o
#OBJS2	:= clientrx.o

COMPC = $(CC)
COMPCC = $(CC)

#CFLAGS += -D$(ENDIANNESS)
ifeq ($(DEBUG), Y)
CFLAGS += -DDEBUG=1 -g
OPTIMIZE = 
else
OPTIMIZE = -O2
endif

INCLUDES = -I. -I../libaic/   

LNFLAGS  = -L../libaic/lib
LIBS	:= -laic -lrt -lpthread -lc

.c.o:
	$(COMPC) $(CFLAGS) $(OPTIMIZE) $(DEFS) $(INCLUDES) -o $@ -c $<

dirs:
	@mkdir -p $(BINDIR)

all: dirs $(BINDIR)/$(PRGNAME) 
#$(BINDIR)/$(PRG2NAME)

$(BINDIR)/$(PRGNAME): $(OBJS)
	@if [ ! -d ../bin ]; then          \
                mkdir ../bin;      \
        fi;
	$(COMPC) $(LNFLAGS) -o $@ $(OBJS) $(LIBS)

#$(BINDIR)/$(PRG2NAME): $(OBJS2)
#	@if [ ! -d ../bin ]; then          \
#               mkdir ../bin;      \
#        fi;
#	$(COMPC) $(LNFLAGS) -o $@ $(OBJS2) $(LIBS)

clean:
	@rm -fv *.o
	@rm -fv $(OBJS:.o=.cc~)
	@rm -fv $(OBJS)
	@rm -fv $(BINDIR)/*

mcm_install_sysroot:

mcm_install_rfs:

aic_test_install:
	mkdir -p ${DESTDIR}/usr/bin/
	install bin/$(PRGNAME) $(DESTDIR)/usr/bin/
	install bin/$(PRG2NAME) $(DESTDIR)/usr/bin/

###############################################################################
