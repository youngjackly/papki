include prorab.mk


this_name := tests

this_cxxflags += -std=c++11
this_cxxflags += -Wall
this_cxxflags += -DDEBUG
this_cxxflags += -fstrict-aliasing #strict aliasing!!!

this_srcs += main.cpp tests.cpp


this_ldlibs += -lpapki -lstdc++

this_ldflags += -L$(d)../../src/

ifeq ($(prorab_os),macosx)
    this_cxxflags += -stdlib=libc++ #this is needed to be able to use c++11 std lib
    this_ldlibs += -lc++
else ifeq ($(prorab_os),windows)
#    this_cxxflags += -I/usr/include -I/usr/local/include
#    this_ldflags += -L/usr/lib -L/usr/local/lib
endif


$(eval $(prorab-build-app))

include $(prorab_this_dir)../test_target.mk

#add dependency on libpapki.so/dll
$(prorab_this_name): $(abspath $(d)../../src/libpapki$(soext))

include $(prorab_this_dir)../test_target.mk


#include makefile for building papki
$(eval $(call prorab-include,$(d)../../src/makefile))
