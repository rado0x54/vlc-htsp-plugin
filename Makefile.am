ACLOCAL_AMFLAGS = -I m4

lib_LTLIBRARIES = libhtsp_plugin.la
libhtsp_plugin_la_SOURCES = \
        src/access.cpp \
        src/discovery.cpp \
        src/helper.cpp \
        src/htsmessage.cpp \
        src/sha1.c \
        src/vlc-htsp-plugin.cpp
libhtsp_plugin_la_CFLAGS = $(VLC_PLUGIN_CFLAGS) -DMODULE_STRING=\"htsp\"
libhtsp_plugin_la_CPPFLAGS = $(libhtsp_plugin_la_CFLAGS)
libhtsp_plugin_la_LIBADD = $(VLC_PLUGIN_LIBS)
libhtsp_plugin_la_LDFLAGS = \
      -avoid-version -module -export-symbol-regex ^vlc_entry
