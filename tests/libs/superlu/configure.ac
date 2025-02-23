#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
#

AC_PREREQ(2.59)
AC_INIT(superlu, 4.3, [https://github.com/openhpc/ohpc])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([foreign])
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])
AC_SUBST([LOG_DRIVER],['$(SHELL) $(top_srcdir)/../../test-driver-ohpc'])

# verify we have necessary environment variables set

AC_MSG_CHECKING([for SUPERLU_DIR environment variable])
if test "x$SUPERLU_DIR" = "x"; then
   AC_MSG_RESULT([no])
   echo
   AC_ERROR([SUPERLU_DIR not defined - please load superlu environment.])
else
   AC_MSG_RESULT([no])
fi

OHPC_COMPILER_FAMILY

# test compilers

AC_PROG_CC
if test "x$LMOD_FAMILY_COMPILER" = "xacfl"; then
   F77=${FC}
fi
AC_PROG_F77
AC_PROG_CXX
# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST

# Define include path and library linkage from environment variables
# which should be provided via module loads.

CFLAGS="-I${SUPERLU_INC} ${CFLAGS}"
FFLAGS="-I${SUPERLU_INC} ${FFLAGS}"
LDFLAGS="-L${SUPERLU_LIB} -lsuperlu ${OHPC_BLAS} ${LDFLAGS}"

# Set subdirectories
AC_CONFIG_FILES(Makefile tests/Makefile)

# Configure
AC_OUTPUT()

echo
echo '-------------------------------------------------- SUMMARY --------------------------------------------------'
echo
echo Package version............... : $PACKAGE-$VERSION
echo OHPC compiler toolchain....... : $LMOD_FAMILY_COMPILER
echo
echo C compiler.................... : `which $CC`
echo C++ compiler.................. : `which $CXX`
echo Fortran compiler ............. : `which $F77`
echo
echo C compiler flags.............. : $CFLAGS
echo C++ compiler flags............ : $CXXFLAGS
echo Fortran compiler flags........ : $FFLAGS
echo LDFLAGS linker flags.......... : $LDFLAGS
echo
echo '-------------------------------------------------------------------------------------------------------------'
