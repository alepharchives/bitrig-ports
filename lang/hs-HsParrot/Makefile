# $OpenBSD: Makefile,v 1.9 2012/10/28 23:30:15 kili Exp $

COMMENT =		Haskell integration with Parrot virtual machine

DISTNAME =		HsParrot-0.0.2.20110925
REVISION =		0
CATEGORIES =		lang devel

# MIT (see comment in HsParrot.cabal)
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES =		lang/ghc
MODGHC_BUILD =		cabal hackage haddock register

BUILD_DEPENDS =		${RUN_DEPENDS}
RUN_DEPENDS =		devel/hs-HsSyck \
			devel/hs-pugs-DrIFT

.include <bsd.port.mk>
