EXTRA_DIST =
CLEANFILES =
DISTCLEANFILES =

include src/Makefile.am
include tests/Makefile.am
include examples/Makefile.am
include doc/Makefile.am

ACLOCAL_AMFLAGS = -I build/autotools/m4 ${ACLOCAL_FLAGS}
DISTCHECK_CONFIGURE_FLAGS = --enable-silent-rules --enable-hardening --enable-optimizations

bsondocdir = ${docdir}
bsondoc_DATA = \
	COPYING \
	NEWS \
	README

EXTRA_DIST += $(bsondoc_DATA)

dist-hook:
	@if test -d "$(srcdir)/.git"; then                              \
          (cd "$(srcdir)" &&                                            \
           $(top_srcdir)/missing --run git log --stat ) > ChangeLog.tmp \
           && mv -f ChangeLog.tmp $(top_distdir)/ChangeLog              \
           || (rm -f ChangeLog.tmp;                                     \
               echo Failed to generate ChangeLog >&2);                  \
	else                                                            \
	  echo A git checkout is required to generate a ChangeLog >&2;  \
	fi

uninstall-local:
	-rm -r $(bsondocdir)
