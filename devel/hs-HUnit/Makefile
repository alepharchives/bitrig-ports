# $OpenBSD: Makefile,v 1.12 2012/10/28 23:26:01 kili Exp $

COMMENT =		unit testing framework for Haskell

DISTNAME =		HUnit-1.2.4.2
REVISION =		0
CATEGORIES =		devel
HOMEPAGE =		http://hunit.sourceforge.net/

MAINTAINER =		Matthias Kilian <kili@openbsd.org>

# BSD3
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES =		lang/ghc

MODGHC_BUILD =		cabal hackage haddock register

do-regress:
.for p in basic-tests extended-tests optimize-1-tests terminal-tests
	cd ${WDKDIR} && ${WRKBUILD}/dist/build/$p/$p
.endfor

.include <bsd.port.mk>
