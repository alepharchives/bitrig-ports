# $OpenBSD: Makefile,v 1.4 2012/11/16 12:46:22 sthen Exp $

COMMENT=	library and tools to program YubiKeys

DISTNAME=	ykpers-1.9.0
REVISION=	0

SHARED_LIBS +=	ykpers-1                  0.0 # 7.3

CATEGORIES=	sysutils security

HOMEPAGE=	http://code.google.com/p/yubikey-personalization/

MAINTAINER=	Stuart Henderson <sthen@openbsd.org>

# BSD
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

WANTLIB += c pthread usb-1.0 yubikey

MASTER_SITES=	http://yubikey-personalization.googlecode.com/files/

LIB_DEPENDS=	devel/libyubikey \
		devel/libusb1>=1.0.9p1

SEPARATE_BUILD=	Yes
USE_LIBTOOL=	Yes
CONFIGURE_STYLE= gnu
MODGNU_CONFIG_GUESS_DIRS=${WRKSRC}/build-aux
CONFIGURE_ARGS=	${CONFIGURE_SHARED}

.include <bsd.port.mk>
