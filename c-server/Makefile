AXIS_USABLE_LIBS = UCLIBC GLIBC
include $(AXIS_TOP_DIR)/tools/build/rules/common.mak

IDIR =../include

PROG1	= server
OBJS1	= server.c	cam_server.c
SHLIB_NAME    = cam_server
PROGS	= $(PROG1)
LDIR =../lib
PKGS = gio-2.0 glib-2.0  axhttp
CFLAGS += $(shell PKG_CONFIG_PATH=$(PKG_CONFIG_LIBDIR) pkg-config --cflags $(PKGS))
LDFLAGS += -lcapture -pthread -lm
LDLIBS += $(shell PKG_CONFIG_PATH=$(PKG_CONFIG_LIBDIR) pkg-config --libs $(PKGS))

CFLAGS	+= -O0 -g 

CFLAGS-y   += -W \
	    -Wformat=2 \
	    -Wpointer-arith \
	    -Wbad-function-cast \
	    -Wstrict-prototypes \
	    -Wmissing-prototypes \
	    -Winline \
	    -Wdisabled-optimization \
	    -Wfloat-equal \
	    -Wall \
	    -Werror

all:	$(PROGS)


$(PROG1): $(OBJS1)
	$(CC) $(CFLAGS) $(LDFLAGS) $^ $(LIBS) $(LDLIBS) -o $@


cflags:
	$(info $(CFLAGS))

ldlibs:
	$(info $(LDLIBS))

ldflags:
	$(info $(LDFLAGS))

clean:
	rm -f $(PROGS) *.o core
