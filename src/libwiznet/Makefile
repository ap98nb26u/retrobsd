TOPSRC          = $(shell cd ../..; pwd)
include $(TOPSRC)/target.mk

CFLAGS          += -O -Wall -Werror

OBJS    	= w5100.o socket.o ethernet.o client.o server.o udp.o

all:    	../libwiznet.a

../libwiznet.a: ${OBJS}
		@$(AR) cru $@ ${OBJS}
		$(RANLIB) $@

install: 	all
		$(INSTALLDIR) $(DESTDIR)/lib
		$(INSTALL) ../libwiznet.a $(DESTDIR)/lib/libwiznet.a
		$(RANLIB) $(DESTDIR)/lib/libwiznet.a

clean:
		rm -f *.o a.out core test errs ../libwiznet*.a
