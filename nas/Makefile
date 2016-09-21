# **********************************************************************
#
# Copyright (c) 2003-2016 ZeroC, Inc. All rights reserved.
#
# **********************************************************************

top_srcdir	= /home/shangrong/project/ice-demos/cpp

SERVER		= server

TARGETS		= $(SERVER)

SLICE_OBJS	= Chat.o


SOBJS		= $(SLICE_OBJS) \
		  ChatSessionI.o \
		  Server.o

OBJS		= $(COBJS) \
		  $(SOBJS)

include $(top_srcdir)/make/Make.rules

CPPFLAGS	:= -I. $(CPPFLAGS)

ifeq ($(BUILD_WITH_ICEE),yes)
    GLACIER2_LIBS = -Wl,-B$(BUILD_DEMOS)
endif
GLACIER2_LIBS	+= -lGlacier2

ifeq ($(BUILD_DEMOS),static)
	$(Q)$(STRIP) --strip-all --remove-section=.comment --remove-section=.note $(@)
endif

$(SERVER): $(SOBJS)
	rm -f $@
	$(CXX) $(LDFLAGS) $(LDEXEFLAGS) -o $@ $(SOBJS) $(GLACIER2_LIBS) $(LIBS)
ifeq ($(BUILD_DEMOS),static)
	$(Q)$(STRIP) --strip-all --remove-section=.comment --remove-section=.note $(@)
endif
