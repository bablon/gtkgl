if NEED_GLEXTPROTO
GL_CFLAGS += -DGL_GLEXT_PROTOTYPES
endif

EXTRA_DIST_GRESOURCES = glarea-gresource.xml

EXTRA_DIST_GLSHADERS = glarea-gl.vs.glsl
EXTRA_DIST_GLSHADERS += glarea-gl.fs.glsl
EXTRA_DIST_GLSHADERS += glarea-gles.vs.glsl
EXTRA_DIST_GLSHADERS += glarea-gles.fs.glsl

EXTRA_DIST = $(EXTRA_DIST_GRESOURCES) $(EXTRA_DIST_GLSHADERS)

GRESOURCE_C_FILES = $(EXTRA_DIST_GRESOURCES:.xml=.c)

bin_PROGRAMS = glarea
dist_glarea_SOURCES = glarea.c
nodist_glarea_SOURCES = glarea-gresource.c
glarea_CFLAGS = $(GTK3_CFLAGS) $(GL_CFLAGS)
glarea_LDADD = $(GTK3_LIBS) $(GL_LIBS) -lm

%.c : $(top_srcdir)/%.xml
	 $(AM_V_GEN)$(GLIB_COMPILE_RESOURCES) $< --sourcedir=$(top_srcdir) --target=$@ --generate-source

CLEANFILES = $(GRESOURCE_C_FILES) config.h.in~

clean-local:
	-rm -rf autom4te.cache
