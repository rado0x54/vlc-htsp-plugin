#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([libhtsp_plugin],[0.1],[web@rado0x54.de])
AM_INIT_AUTOMAKE(subdir-objects foreign)
AC_CONFIG_SRCDIR([src/access.cpp])
AC_CONFIG_HEADERS([config.h])

AC_CONFIG_MACRO_DIRS([m4])

# Checks for programs.
AC_LANG([C])
AC_LANG([C++])

AX_CXX_COMPILE_STDCXX(11)

LT_INIT([dlopen win32-dll shared disable-static])

PKG_PROG_PKG_CONFIG

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([stdint.h string.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_CHECK_HEADER_STDBOOL
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_FUNC_MALLOC
AC_CHECK_FUNCS([memset])



HAVE_INT_VLC_PLUGIN=true;

PKG_CHECK_MODULES(VLC_PLUGIN, [vlc-plugin >= 2.2.0], 
        [HAVE_INT_VLC_PLUGIN=false],[:])

if ${HAVE_INT_VLC_PLUGIN}; then
    BUILD_DIR=`pwd`
    VLC_DEP_DIR=${BUILD_DIR}/vlc_deps
    AC_MSG_RESULT([No vlc-plugin found. Expecting installation at ${VLC_DEP_DIR}])
    VLC_PLUGIN_INCLUDE_DIR=${VLC_DEP_DIR}/include/vlc
    VLC_PLUGIN_LIB_DIR=${VLC_DEP_DIR}/lib
    VLC_PLUGIN_CFLAGS="-I${VLC_PLUGIN_INCLUDE_DIR} -I${VLC_PLUGIN_INCLUDE_DIR}/plugins -D__PLUGIN__ -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_THREAD_SAFE"
    VLC_PLUGIN_LIBS="-L${VLC_PLUGIN_LIB_DIR} -lvlccore"
    AC_SUBST(VLC_PLUGIN_CFLAGS)
    AC_SUBST(VLC_PLUGIN_LIBS)
fi


AC_SUBST(LIBEXT)

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
