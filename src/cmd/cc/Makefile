TOPSRC		= $(shell cd ../../..; pwd)
include $(TOPSRC)/target.mk
#include $(TOPSRC)/cross.mk

OBJS            = cc.o

CFLAGS		+= -Werror -Wall
# avoid problems with cygpath in msys environment. see cc.c also.
CFLAGS          += -DVERSSTR=\"1.0\"
ifneq ($(origin __MSYS__),undefined)
CFLAGS          += -DSTDINC=\"/include\" \
                   -DLIBDIR=\"/lib\" \
                   -DLIBEXECDIR=\"/libexec\" \
                   -DCRT0FILE=\"/lib/crt0.o\" \
                   -DCRT0FILE_PROFILE=\"/lib/mcrt0.o\"
endif

all:            cc

cc:             $(OBJS)
		${CC} ${LDFLAGS} -o cc.elf $(OBJS) ${LIBS}
		${OBJDUMP} -S cc.elf > cc.dis
		${SIZE} cc.elf
		${ELF2AOUT} cc.elf $@ && rm cc.elf

clean:
		rm -f *.o *.0 *.elf cc *.elf *.dis tags *~

install:        all
		install cc $(DESTDIR)/bin/
		install cc $(DESTDIR)/bin/scc
		install cc $(DESTDIR)/bin/lcc
