# $OpenBSD: Makefile,v 1.6 2012/10/28 23:26:37 kili Exp $

COMMENT=		fast base64 encodings and decoding for ByteStrings

DISTNAME=		base64-bytestring-1.0.0.0
REVISION=		0
CATEGORIES=		devel

MAINTAINER=		Jasper Lievisse Adriaanse <jasper@openbsd.org>

# 3-clause BSD
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MODULES=		lang/ghc

MODGHC_BUILD =          cabal hackage haddock register

.include <bsd.port.mk>
