# $OpenBSD: Makefile,v 1.8 2012/10/11 14:39:45 dcoppa Exp $

BROKEN =		overlapping instances with hs-parsec >= 3.0
COMMENT =		Perl 6 Implementation

DISTNAME =		Pugs-6.2.13.15
REVISION =		3
CATEGORIES =		lang devel
HOMEPAGE =		http://pugscode.org/

# BSD3
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

VMEM_WARNING =		Yes

WANTLIB =		c m ncursesw perl pthread util

MODULES =		lang/ghc converters/libiconv

# XXX nort may be wrong here, in case pugs uses ghci or ghc at runtime.
MODGHC_BUILD =		cabal hackage nort

BUILD_DEPENDS =		devel/hs-binary \
			devel/hs-control-timeout>=0.1.2 \
			devel/hs-FindBin \
			lang/hs-HsParrot>=0.0.2 \
			devel/hs-HsSyck>=0.44 \
			devel/hs-MetaObject>=0.0.4 \
			devel/hs-parsec<3.0.0 \
			devel/hs-pugs-compat>=0.0.5 \
			devel/hs-pugs-DrIFT>=2.2.3.0 \
			devel/hs-stringtable-atom>=0.0.4

.include <bsd.port.mk>
