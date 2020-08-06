AC_INIT([gtkgl], [0.1])
AC_CONFIG_HEADERS([config.h])

AM_INIT_AUTOMAKE([foreign -Wall])
AM_SILENT_RULES([yes])

AC_PROG_CC

AC_PATH_PROG(GLIB_COMPILE_RESOURCES, glib-compile-resources)
if test "xGLIB_COMPILE_RESOURCES" = "x"; then
	AC_MSG_ERROR("glib-compile-resources is not found.")
fi

PKG_CHECK_MODULES(GTK3, [gtk+-3.0])
PKG_CHECK_MODULES(GL, [gl])

AC_CHECK_HEADER([GL/glcorearb.h], [], AC_MSG_ERROR(["GL/glcorearb.h is needed."]))
AC_CHECK_DECL(GL_GLEXT_PROTOTYPES, [need_glextproto=no], [need_glextproto=yes], [[#include <GL/glcorearb.h>]])
AM_CONDITIONAL(NEED_GLEXTPROTO, test "x$need_glextproto" = "xyes")

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
