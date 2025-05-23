USE_COLLECT2 = ld
MAYBE_USE_COLLECT2 = -DUSE_COLLECT2
VPATH = ../../gcc-2.7.2.3/cp
# Makefile for GNU C++ compiler.
#   Copyright (C) 1987, 88, 90-4, 1995 Free Software Foundation, Inc.

#This file is part of GNU CC.

#GNU CC is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 2, or (at your option)
#any later version.

#GNU CC is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with GNU CC; see the file COPYING.  If not, write to
#the Free Software Foundation, 59 Temple Place - Suite 330,
#Boston, MA 02111-1307, USA.

# The makefile built from this file lives in the language subdirectory.
# Its purpose is to provide support for:
#
# 1) recursion where necessary, and only then (building .o's), and
# 2) building and debugging cc1 from the language subdirectory, and
# 3) nothing else.
#
# The parent makefile handles all other chores, with help from the
# language makefile fragment, of course.
#
# The targets for external use are:
# all, TAGS, ???mostlyclean, ???clean.

# Suppress smart makes who think they know how to automake Yacc files
.y.c:

# Variables that exist for you to override.
# See below for how to change them for certain systems.

ALLOCA =

# Various ways of specifying flags for compilations:  
# CFLAGS is for the user to override to, e.g., do a bootstrap with -O2.
# BOOT_CFLAGS is the value of CFLAGS to pass
# to the stage2 and stage3 compilations
# XCFLAGS is used for most compilations but not when using the GCC just built.
XCFLAGS =
CFLAGS = -g
BOOT_CFLAGS = -O $(CFLAGS)
# These exists to be overridden by the x-* and t-* files, respectively.
X_CFLAGS =
T_CFLAGS =

X_CPPFLAGS =
T_CPPFLAGS =

CC = cc
BISON = bison
BISONFLAGS =
LEX = flex
LEXFLAGS =
AR = ar
AR_FLAGS = rc
SHELL = /bin/sh
MAKEINFO = makeinfo
TEXI2DVI = texi2dvi

# Define this as & to perform parallel make on a Sequent.
# Note that this has some bugs, and it seems currently necessary 
# to compile all the gen* files first by hand to avoid erroneous results.
P =

# This is used in the definition of SUBDIR_USE_ALLOCA.
# ??? Perhaps it would be better if it just looked for *gcc*.
OLDCC = cc

# This is used instead of ALL_CFLAGS when compiling with GCC_FOR_TARGET.
# It omits XCFLAGS, and specifies -B./.
# It also specifies -B$(tooldir)/ to find as and ld for a cross compiler.
GCC_CFLAGS=$(INTERNAL_CFLAGS) $(X_CFLAGS) $(T_CFLAGS) $(CFLAGS)

# Tools to use when building a cross-compiler.
# These are used because `configure' appends `cross-make'
# to the makefile when making a cross-compiler.

target=sslittle-na-sstrix
xmake_file=ss/x-sstrix
tmake_file=ss/t-ss-gas
#version=`sed -e 's/.*\"\([^ \"]*\)[ \"].*/\1/' < $(srcdir)/version.c`
#mainversion=`sed -e 's/.*\"\([0-9]*\.[0-9]*\).*/\1/' < $(srcdir)/version.c`

# Directory where sources are, from where we are.
srcdir = ../../gcc-2.7.2.3/cp

# Additional system libraries to link with.
CLIB=

# Change this to a null string if obstacks are installed in the
# system library.
OBSTACK=obstack.o

# Choose the real default target.
ALL=all

# End of variables for you to override.

# Definition of `all' is here so that new rules inserted by sed
# do not specify the default target.
all: all.indirect

# This tells GNU Make version 3 not to put all variables in the environment.
.NOEXPORT:

# sed inserts variable overrides after the following line.
####target overrides
#
# $Log: t-ss-gas,v $
# Revision 1.1  1994/01/20  16:17:32  austin
# Initial revision
#
#  $Id: t-ss-gas,v 1.1 1994/01/20 16:17:32 austin Exp austin $
#

# Suppress building libgcc1.a, since the SS compiler port is complete
# and does not need anything from libgcc1.a.
LIBGCC1 = libgcc1.null
CROSS_LIBGCC1 = libgcc1.null
#T_CFLAGS = -Dinhibit_libc
####host overrides
#
# $Log: x-sstrix,v $
# Revision 1.1  1994/01/20  16:17:49  austin
# Initial revision
#
# $Id: x-sstrix,v 1.1 1994/01/20 16:17:49 austin Exp austin $
#

# Define CC and OLDCC as the same, so that the tests:
#	if [ x"$(OLDCC)" = x"$(CC)" ] ...
#
# will succeed (if OLDCC != CC, it is assumed that GCC is
# being used in secondary stage builds).  We need to pass
# the -Wf,-XNg1500 option so the compiler can compile the
# G++ file cp-parse.c.  Otherwise it complains about
# too many case statements.  -Olimit is so the user
# can use -O2.  Down with fixed size tables!

CC		= $(OLDCC)
OPT		= -O1
OLDCC		= cc -Wf,-XNg1500 -Olimit 3000 $(OPT)

# The bison output files are machine-indep,
# so different flags for a particular machine are not useful.
#BISONFLAGS	= -l
####cross overrides
####build overrides

# Now figure out from those variables how to compile and link.

all.indirect: Makefile ../cc1plus

# IN_GCC tells obstack.h that we are using gcc's <stddef.h> file.
INTERNAL_CFLAGS = $(CROSS) -DIN_GCC

# This is the variable actually used when we compile.
ALL_CFLAGS = $(INTERNAL_CFLAGS) $(X_CFLAGS) $(T_CFLAGS) $(CFLAGS) $(XCFLAGS)

# Likewise.
ALL_CPPFLAGS = $(CPPFLAGS) $(X_CPPFLAGS) $(T_CPPFLAGS)

# Even if ALLOCA is set, don't use it if compiling with GCC.

SUBDIR_OBSTACK = `if [ x$(OBSTACK) != x ]; then echo ../$(OBSTACK); else true; fi`
SUBDIR_USE_ALLOCA = `case "${CC}" in "${OLDCC}") if [ x$(ALLOCA) != x ]; then echo ../$(ALLOCA); else true; fi ;; esac`
SUBDIR_MALLOC = `if [ x$(MALLOC) != x ]; then echo ../$(MALLOC); else true; fi`

# How to link with both our special library facilities
# and the system's installed libraries.
LIBS = $(SUBDIR_OBSTACK) $(SUBDIR_USE_ALLOCA) $(SUBDIR_MALLOC) $(CLIB)

# Specify the directories to be searched for header files.
# Both . and srcdir are used, in that order,
# so that tm.h and config.h will be found in the compilation
# subdirectory rather than in the source directory.
INCLUDES = -I. -I.. -I$(srcdir) -I$(srcdir)/.. -I$(srcdir)/../config

# Always use -I$(srcdir)/config when compiling.
.c.o:
	$(CC) -c $(ALL_CFLAGS) $(ALL_CPPFLAGS) $(INCLUDES) $<

# This tells GNU make version 3 not to export all the variables
# defined in this file into the environment.
.NOEXPORT:

# Lists of files for various purposes.

# Language-specific object files for g++

CXX_OBJS = call.o decl.o errfn.o expr.o pt.o sig.o typeck2.o \
 class.o decl2.o error.o gc.o lex.o parse.o ptree.o spew.o typeck.o cvt.o \
 edsel.o except.o init.o method.o search.o tree.o xref.o repo.o

# Language-independent object files.
OBJS = `cat ../stamp-objlist` ../c-common.o ../c-pragma.o
OBJDEPS = ../stamp-objlist ../c-common.o ../c-pragma.o

compiler: ../cc1plus
../cc1plus: $(P) $(CXX_OBJS) $(OBJDEPS) $(LIBDEPS)
	rm -f ../cc1plus$(exeext)
	$(CC) $(ALL_CFLAGS) $(LDFLAGS) -o $@ \
	      $(CXX_OBJS) $(OBJS) $(LIBS)

Makefile: $(srcdir)/Makefile.in $(srcdir)/../configure
	cd ..; $(SHELL) config.status

native: config.status ../cc1plus

# Compiling object files from source files.

# Note that dependencies on obstack.h are not written
# because that file is not part of GCC.

# C++ language specific files.

RTL_H = $(srcdir)/../rtl.h $(srcdir)/../rtl.def \
	$(srcdir)/../machmode.h $(srcdir)/../machmode.def
TREE_H = $(srcdir)/../tree.h $(srcdir)/../real.h $(srcdir)/../tree.def \
	$(srcdir)/../machmode.h $(srcdir)/../machmode.def
CXX_TREE_H = $(TREE_H) cp-tree.h tree.def
PARSE_H = $(srcdir)/parse.h
PARSE_C = $(srcdir)/parse.c

parse.o : $(PARSE_C) $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h lex.h
	$(CC) -c $(ALL_CFLAGS) $(ALL_CPPFLAGS) $(INCLUDES) $(BIG_SWITCHFLAG) \
  `echo $(PARSE_C) | sed 's,^\./,,'`

CONFLICTS = expect 5 shift/reduce conflicts and 38 reduce/reduce conflicts.
$(PARSE_H) : $(PARSE_C)
$(PARSE_C) : $(srcdir)/parse.y
	@echo $(CONFLICTS)
	cd $(srcdir); $(BISON) $(BISONFLAGS) -d -o parse.c parse.y
	cd $(srcdir); grep '^#define[ 	]*YYEMPTY' parse.c >>parse.h
#$(PARSE_C) $(PARSE_H) : stamp-parse ; @true
#stamp-parse: $(srcdir)/parse.y
#	@echo $(CONFLICTS)
#	$(BISON) $(BISONFLAGS) -d $(srcdir)/parse.y
#	grep '^#define[ 	]*YYEMPTY' y.tab.c >>y.tab.h
#	$(srcdir)/../move-if-change y.tab.c $(PARSE_C)
#	$(srcdir)/../move-if-change y.tab.h $(PARSE_H)
#	cp $(PARSE_C) y.tab.c
#	touch stamp-parse

# hash.h really depends on $(srcdir)/gxx.gperf.
# But this would screw things for people that don't have gperf,
# if gxx.gpref got touched, say.
# Thus you have to remove hash.h to force it to be re-made.
$(srcdir)/hash.h:
	gperf -p -j1 -g -o -t -N is_reserved_word '-k1,4,7,$$' \
		$(srcdir)/gxx.gperf >$(srcdir)/hash.h

spew.o : spew.c $(CONFIG_H) $(CXX_TREE_H) \
  $(PARSE_H) $(srcdir)/../flags.h lex.h
lex.o : lex.c $(CONFIG_H) $(CXX_TREE_H) \
  $(PARSE_H) input.c $(srcdir)/../flags.h hash.h lex.h $(srcdir)/../c-pragma.h
decl.o : decl.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h \
  lex.h decl.h $(srcdir)/../stack.h
decl2.o : decl2.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h \
  lex.h decl.h
typeck2.o : typeck2.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h
typeck.o : typeck.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h $(RTL_H)
class.o : class.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h
call.o : call.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h class.h
init.o : init.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h $(RTL_H)
method.o : method.c $(CONFIG_H) $(CXX_TREE_H) class.h
cvt.o : cvt.c $(CONFIG_H) $(CXX_TREE_H) class.h
search.o : search.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../stack.h $(srcdir)/../flags.h
tree.o : tree.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h
ptree.o : ptree.c $(CONFIG_H) $(CXX_TREE_H)
gc.o : gc.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h
except.o : except.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h $(RTL_H)
expr.o : expr.c $(CONFIG_H) $(CXX_TREE_H) $(RTL_H) $(srcdir)/../flags.h \
  $(srcdir)/../expr.h ../insn-codes.h
edsel.o : edsel.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../stack.h $(srcdir)/../flags.h
xref.o : xref.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../input.h
pt.o : pt.c $(CONFIG_H) $(CXX_TREE_H) decl.h $(PARSE_H)
error.o : error.c $(CONFIG_H) $(CXX_TREE_H)
errfn.o : errfn.c $(CONFIG_H) $(CXX_TREE_H)
sig.o : sig.c $(CONFIG_H) $(CXX_TREE_H) $(srcdir)/../flags.h
repo.o : repo.c $(CONFIG_H) $(CXX_TREE_H)

# These exist for maintenance purposes.

# Update the tags table.
TAGS: force
	cd $(srcdir) ;				\
	etags *.c *.h ;				\
	echo 'l' | tr 'l' '\f' >> TAGS ;	\
	echo 'parse.y,0' >> TAGS ; 		\
	etags -a ../*.h ../*.c;

.PHONY: TAGS

force:
