# $OpenBSD: Makefile,v 1.1.1.1 2012/10/31 19:16:55 kili Exp $

COMMENT =		constraint manipulation

DISTNAME=		constraints-0.3.2
CATEGORIES =		devel

# BSD3
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES =		lang/ghc

MODGHC_BUILD =		cabal hackage haddock register

BUILD_DEPENDS =		${RUN_DEPENDS}
RUN_DEPENDS =		devel/hs-newtype>=0.2,<0.3

.include <bsd.port.mk>
