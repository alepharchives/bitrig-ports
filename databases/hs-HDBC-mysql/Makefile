# $OpenBSD: Makefile,v 1.9 2012/10/28 23:24:28 kili Exp $

COMMENT=		mysql driver for HDBC

DISTNAME=		HDBC-mysql-0.6.6.0
REVISION=		0
CATEGORIES=		databases

HOMEPAGE=		https://github.com/bos/hdbc-mysql

MAINTAINER=		David Coppa <dcoppa@openbsd.org>

# LGPLv2
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES=		lang/ghc

MODGHC_BUILD=		cabal hackage haddock register

RUN_DEPENDS +=		databases/hs-HDBC>=2.1.0 \
			databases/mysql \
			devel/hs-mtl
BUILD_DEPENDS +=	${RUN_DEPENDS}

.include <bsd.port.mk>
