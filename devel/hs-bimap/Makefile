# $OpenBSD: Makefile,v 1.4 2012/10/28 23:26:37 kili Exp $

COMMENT=		bidirectional mapping between two key types

DISTNAME=		bimap-0.2.4
REVISION=		2
CATEGORIES=		devel

MAINTAINER=		Matthias Kilian <kili@openbsd.org>

# BSD3
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

MODULES=		lang/ghc

MODGHC_BUILD=		cabal hackage haddock register

.include <bsd.port.mk>
