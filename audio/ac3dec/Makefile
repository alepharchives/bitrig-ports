# $OpenBSD: Makefile,v 1.17 2012/08/19 22:30:37 ajacoutot Exp $

COMMENT=	ac3 audio (as used on DVDs) decoding tools

DISTNAME=	ac3dec-0.6.1
REVISION=	1
CATEGORIES=	audio

HOMEPAGE=	http://liba52.sourceforge.net/

# GPL
PERMIT_PACKAGE_CDROM=   Yes
PERMIT_PACKAGE_FTP=     Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=   Yes

WANTLIB=		c m ossaudio

MASTER_SITES=	http://liba52.sourceforge.net/files/

CONFIGURE_STYLE= gnu
MODGNU_CONFIG_GUESS_DIRS= ${WRKSRC}/

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/ac3dec
	${INSTALL_DATA} ${WRKSRC}/README ${PREFIX}/share/doc/ac3dec
	${INSTALL_DATA} ${WRKSRC}/TODO ${PREFIX}/share/doc/ac3dec

.include <bsd.port.mk>
