# $OpenBSD: Makefile,v 1.11 2012/10/13 10:40:38 jasper Exp $

COMMENT=		C macros to add, find and delete items from a hash

DISTNAME=		uthash-1.9.7
CATEGORIES=		devel

HOMEPAGE=		http://uthash.sf.net/

# BSD
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

MASTER_SITES=		${MASTER_SITE_SOURCEFORGE:=uthash/}
EXTRACT_SUFX=		.tar.bz2

NO_BUILD=		Yes
PKG_ARCH=		*

PORTHOME=		/tmp
REGRESS_TARGET= 	run_tests

do-install:
	${INSTALL_DATA} ${WRKSRC}/src/*.h ${PREFIX}/include
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/uthash/img
	${INSTALL_DATA} ${WRKSRC}/doc/html/*.{css,html} \
		${PREFIX}/share/doc/uthash
	${INSTALL_DATA} ${WRKSRC}/doc/html/img/* ${PREFIX}/share/doc/uthash/img

do-regress:
	@cd ${WRKSRC}/tests/ && exec ${SETENV} ${MAKE_ENV} \
		${MAKE_PROGRAM} ${REGRESS_FLAGS} -f ${MAKE_FILE} \
		${REGRESS_TARGET}

.include <bsd.port.mk>
