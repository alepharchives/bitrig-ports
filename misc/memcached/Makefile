# $OpenBSD: Makefile,v 1.18 2012/08/23 17:51:22 ajacoutot Exp $

COMMENT=	distributed memory object caching system

DISTNAME =	memcached-1.4.13
CATEGORIES=	misc
REVISION=	0

HOMEPAGE=	http://www.memcached.org/

MAINTAINER=	Scott Vokes <vokes.s@gmail.com>

# BSD
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

WANTLIB=		c event pthread

MASTER_SITES=		http://memcached.googlecode.com/files/
MASTER_SITES0=		${HOMEPAGE}/dist/

CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS=		--with-libevent=/usr --disable-coverage

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/memcached
	${INSTALL_DATA} ${WRKSRC}/doc/*.txt ${PREFIX}/share/doc/memcached

.include <bsd.port.mk>
