# **********************************************************************
#
# Copyright (c) 2003-2016 ZeroC, Inc. All rights reserved.
#
# **********************************************************************

top_srcdir	= /home/shangrong/project/ice-demos/cpp

CLIENT		= client

TARGETS		= $(CLIENT) 

SLICE_OBJS	= Chat.o

COBJS		= $(SLICE_OBJS) \
		  Client.o


OBJS		= $(COBJS) \
		  $(SOBJS)

include $(top_srcdir)/make/Make.rules

CPPFLAGS	:= -I. $(CPPFLAGS)

ifeq ($(BUILD_WITH_ICEE),yes)
    GLACIER2_LIBS = -Wl,-B$(BUILD_DEMOS)
endif
GLACIER2_LIBS	+= -lGlacier2

$(CLIENT): $(COBJS)
	rm -f $@
	$(CXX) $(LDFLAGS) $(LDEXEFLAGS) -o $@ $(COBJS) $(GLACIER2_LIBS) $(LIBS)
ifeq ($(BUILD_DEMOS),static)
	$(Q)$(STRIP) --strip-all --remove-section=.comment --remove-section=.note $(@)
endif

ifeq ($(BUILD_DEMOS),static)
	$(Q)$(STRIP) --strip-all --remove-section=.comment --remove-section=.note $(@)
endif
