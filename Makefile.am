## Process this file with automake to produce Makefile.in

####################################################################################################

all:
if COMPILE_PTLIB
	($(MAKE) $(MAKEFLAGS) @PTLIB_BUILDOPTS@    -C @PTLIBDIR@) || exit $$?
	($(MAKE) $(MAKEFLAGS) @H323PLUS_BUILDOPTS@ -C @H323PLUSDIR@) || exit $$?
endif
if COMPILE_LIBG7221
	($(MAKE) $(MAKEFLAGS)     -C @LIBG7221_DIR@) || exit $$?
endif
	($(MAKE) $(MAKEFLAGS) @MCU_BUILDOPTS@      -C @MCUDIR@) || exit $$?
	( for dir in @PLUGIN_DIRS@; \
		do ($(MAKE) $(MAKEFLAGS) -C $$dir) || exit $$?; \
	done )

####################################################################################################

install:
	($(MAKE) install -C @MCUDIR@) || exit $$?
	( for dir in @PLUGIN_DIRS@; \
		do ($(MAKE) install -C $$dir) || exit $$?; \
	done )
if COMPILE_PTLIB
if COMPILE_PTLIB_NO_STATIC
	install -m 644 @PTLIB_BUILDDIR@/@PTLIB_SO_FILE@ $(DESTDIR)@MCU_LIB_DIR@
	install -m 644 @H323PLUS_BUILDDIR@/@H323PLUS_SO_FILE@ $(DESTDIR)@MCU_LIB_DIR@
endif
endif

####################################################################################################

uninstall:
	($(MAKE) uninstall -C @MCUDIR@) || exit $$?
	( for dir in @PLUGIN_DIRS@; \
		do ($(MAKE) uninstall -C $$dir) || exit $$?; \
	done )
if COMPILE_PTLIB
if COMPILE_PTLIB_NO_STATIC
	rm -f $(DESTDIR)@MCU_LIB_DIR@/@PTLIB_SO_FILE@
	rm -f $(DESTDIR)@MCU_LIB_DIR@/@H323PLUS_SO_FILE@
endif
endif

####################################################################################################

clean:
if COMPILE_LIBG7221
	($(MAKE) clean -C @LIBG7221_DIR@) || exit $$?
endif
if COMPILE_PTLIB
	($(MAKE) clean -C @PTLIBDIR@) || exit $$?
	($(MAKE) clean -C @H323PLUSDIR@) || exit $$?
endif
	($(MAKE) clean -C @MCUDIR@) || exit $$?
	( for dir in @PLUGIN_DIRS@; \
		do ($(MAKE) clean -C $$dir) || exit $$?; \
	done )

####################################################################################################
