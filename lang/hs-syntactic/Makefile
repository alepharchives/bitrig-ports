# $OpenBSD: Makefile,v 1.1.1.1 2012/10/31 19:21:14 kili Exp $

COMMENT =		abstract syntax and utilities for embedded languages

DISTNAME =		syntactic-1.4
CATEGORIES =		devel lang

# BSD3
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES =		lang/ghc

MODGHC_BUILD =		cabal hackage haddock register

BUILD_DEPENDS =		${RUN_DEPENDS}
RUN_DEPENDS =		devel/hs-constraints \
			devel/hs-data-hash \
			devel/hs-mtl>=2,<3 \
			devel/hs-transformers>=0.2 \
			devel/hs-tuple>=0.2

.include <bsd.port.mk>
