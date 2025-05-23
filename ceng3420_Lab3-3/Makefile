# /***************************************************************/
# /*                                                             */
# /*                  RISCV-LC Simulator                         */
# /*                                                             */
# /*                     CEG3420 Lab3                            */
# /*                 cbai@cse.cuhk.edu.hk                        */
# /*           The Chinese University of Hong Kong               */
# /*                                                             */
# /***************************************************************/

OS := $(shell uname -s)
ARCH := $(shell uname -m)
SRC := $(shell find . -name "*.c")
TGT := riscv-lc
LIB := lib$(TGT).a
OPT := -Wall -std=c99 -Wno-return-type -O3 -fPIC -fno-pie -no-pie


ifeq ($(OS), Darwin)
	lib_path = ./tools/macos/$(ARCH)
else ifeq ($(OS), Linux)
	REL := $(shell lsb_release -si)
	VER := $(shell lsb_release -sr)
	ifeq ($(REL), Ubuntu)
		lib_path = ./tools/linux/ubuntu/$(VER)
	else
		lib_path = ./tools/linux/centos
	endif
else ifeq (MINGW64, $(findstring MINGW64, $(OS)))
	lib_path = ./tools/win
	CC = gcc
endif

.default: all

all: $(TGT)

$(TGT): $(SRC)
	$(CC) $(OPT) $^ $(lib_path)/$(LIB) -o $@

.PHONY: clean
clean:
	rm -f $(TGT)
