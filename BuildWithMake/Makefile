# Hey emacs, this is a -*- makefile -*-

# Copyright (c) Stanford University, The Regents of the University of
#               California, and others.
#
# All Rights Reserved.
#
# See Copyright-SimVascular.txt for additional details.
#
# Permission is hereby granted, free of charge, to any person obtaining
# a copy of this software and associated documentation files (the
# "Software"), to deal in the Software without restriction, including
# without limitation the rights to use, copy, modify, merge, publish,
# distribute, sublicense, and/or sell copies of the Software, and to
# permit persons to whom the Software is furnished to do so, subject
# to the following conditions:
#
# The above copyright notice and this permission notice shall be included
# in all copies or substantial portions of the Software.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS
# IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED
# TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
# PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER
# OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
# EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
# PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
# PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
# LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
# NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
# SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

TOP=$(SV_TOP)

include $(TOP)/include.mk

PLUGIN_TOP_DIRS = ../Code/Source/sv4gui/Plugins

all-shared: shared-pre-build all-shared-build-only

all-shared-build-only: shared

fast:
	-make shared-pre-build
	-make -j6 all-shared-build-only
	make all-shared-build-only

common-pre-build:
	mkdir -p Bin
	mkdir -p Lib
	mkdir -p Bin/plugins
	mkdir -p ../Code/Source/Include/Make

shared-pre-build: common-pre-build
	for i in ${PLUGIN_TOP_DIRS}; do ( \
	  cd $$i; \
	  $(MAKE) pre-shared-build ) ; done

shared:
	for i in ${PLUGIN_TOP_DIRS}; do ( \
	  cd $$i; \
	  $(MAKE) shared ) ; done

clean:
	for i in ${PLUGIN_TOP_DIRS}; do ( \
	  cd $$i; \
	  $(MAKE) clean ) ; done

veryclean: clean
	for i in ${PLUGIN_TOP_DIRS}; do ( \
	  cd $$i; \
	  $(MAKE) veryclean ) ; done