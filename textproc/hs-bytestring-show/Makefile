# $OpenBSD: Makefile,v 1.8 2012/10/28 23:31:14 kili Exp $

COMMENT =		efficient conversion of values to readable byte strings

DISTNAME =		bytestring-show-0.3.5.1
REVISION =		0
CATEGORIES =		textproc

MAINTAINER =		Jim Razmus II <jim@openbsd.org>

# BSD3
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES =		lang/ghc

MODGHC_BUILD =		cabal hackage haddock register

RUN_DEPENDS +=		devel/hs-binary
BUILD_DEPENDS +=	${RUN_DEPENDS}

.include <bsd.port.mk>
