dnl Process this file with autoconf to produce a configure script.
AC_INIT(libnss_nis, 3.0)
AM_INIT_AUTOMAKE
AC_CONFIG_SRCDIR([src/nss-nis.c])
AM_CONFIG_HEADER(config.h)
AC_CONFIG_MACRO_DIR([m4])
AC_PREFIX_DEFAULT(/usr)

AC_SUBST(PACKAGE)
AC_SUBST(VERSION)

dnl Checks for programs.
AC_PROG_CC
AC_GNU_SOURCE
AM_PROG_CC_C_O
dnl If we're using gcc, we want warning flags
dnl test -n "$GCC" && WARNFLAGS="-Wall"
test -n "$GCC" && WARNFLAGS="-W -Wall -Wbad-function-cast -Wcast-align -Winline -Wnested-externs -Wshadow -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wundef -Werror"
AC_SUBST(WARNFLAGS)
AC_PROG_CPP
AC_ISC_POSIX
AC_PROG_INSTALL
AC_PROG_MAKE_SET
AC_PROG_LIBTOOL
LT_INIT

dnl Checks for libraries.
PKG_CHECK_MODULES([TIRPC], [libtirpc], [], [TIRPC_LIBS=""])
old_CFLAGS=$CFLAGS
old_LIBS=$LIBS
old_CPPFLAGS=$CPPFLAGS
CFLAGS="$CFLAGS $TIRPC_CFLAGS"
LIBS="$LIBS $TIRPC_LIBS"
CPPFLAGS="$CPPFLAGS $TIRPC_CFLAGS"
AC_CHECK_HEADERS([rpc/netdb.h rpc/rpcent.h])
AC_CHECK_FUNCS([xdecrypt])
CFLAGS=$old_CFLAGS
LIBS=$old_LIBS
CPPFLAGS=$old_CPPFLAGS

PKG_CHECK_MODULES([LIBNSL], [libnsl], [], [AC_CHECK_LIB([nsl],[yp_match],[LIBNSL_LIBS="-lnsl"],[LIBNSL_LIBS=""])])

AC_OUTPUT([Makefile src/Makefile])
