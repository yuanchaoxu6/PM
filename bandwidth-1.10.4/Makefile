#============================================================================
# bandwidth, a benchmark to estimate memory transfer bandwidth.
# Copyright (C) 2005-2020 by Zack T Smith.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
# The author may be reached at veritas@comcast.net.
#============================================================================

# Note: 32-bit is no longer supported by Mac OS.

OOCLIB32=OOC/OOC32.a
OOCLIB64=OOC/OOC64.a

UNAMESYS := $(shell uname -s)
UNAMEPROC := $(shell uname -p)
UNAMEMACHINE := $(shell uname -m)

ifeq (${UNAMESYS},Linux)
	ifeq (${UNAMEPROC},armv7l)
		include Makefile-arm32
	else ifeq (${UNAMEMACHINE},armv7l)
		include Makefile-arm32
	else ifeq (${UNAMEMACHINE},aarch64)
		include Makefile-arm64
	else ifeq (${UNAMEPROC},i386)
		include Makefile-linux-i386
	else ifeq (${UNAMEPROC},x86_64)
		include Makefile-linux-x86_64
	endif
else ifeq (${UNAMESYS},Darwin)
	ifeq (${UNAMEMACHINE},arm64)
		include Makefile-arm64
	else
		include Makefile-darwin-x86_64
	endif
else ifeq (${UNAMESYS},Windows)
	include Makefile-windows
endif

message:
	@echo "To compile for 32-bit i386 Linux:     make -f Makefile-linux bandwidth32"
	@echo "To compile for 64-bit x86_64 Linux:   make -f Makefile-linux bandwidth64"
	@echo "To compile for 32-bit ARM Linux:      make -f Makefile-arm32 bandwidth32"
	@echo "To compile for 64-bit ARM Linux:      make -f Makefile-arm64 bandwidth64"
	@echo "To compile for 64-bit x86 Mac OS/X:   make -f Makefile-darwin bandwidth64"
	@echo "To compile for 64-bit Windows+Cygwin: make -f Makefile-windows bandwidth64"
	@echo "To compile for 32-bit Windows+Cygwin: make -f Makefile-windows bandwidth32"

clean:
	rm -f main.o bandwidth bandwidth32 bandwidth64 routines-x86-32bit.o routines-x86-64bit.o 
	rm -f Testing.o CPUCharacteristics.o
	rm -f bandwidth32.exe bandwidth64.exe
	rm -f utility-x86-32bit.o utility-x86-64bit.o
	rm -f bandwidth.bmp bandwidth32 bandwidth64 bandwidth-arm32 bandwidth-arm64
	rm -f routines-arm-32bit.o routines-arm-64bit.o 
	rm -f routines-arm-rpi-32bit.o routines-arm-rpi-64bit.o 
	rm -rf bandwidth64.dSYM bandwidth32.dSYM
	( cd OOC; make clean )
	rm -f Makefile-flags

