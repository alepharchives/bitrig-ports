# $OpenBSD: Makefile,v 1.1.1.1 2012/11/19 22:14:52 sthen Exp $

COMMENT =		utility for creating secure pipes between socket addresses

DISTNAME =		spiped-1.2.2
CATEGORIES =		security sysutils

MAINTAINER =		James Turner <james@calminferno.net>

HOMEPAGE =		http://www.tarsnap.com/spiped.html
MASTER_SITES =		http://www.tarsnap.com/spiped/

# BSD
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

WANTLIB =		c crypto pthread

EXTRACT_SUFX =		.tgz
NO_REGRESS =		Yes
FAKE_FLAGS =		BINDIR="${WRKINST}${PREFIX}/bin"

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/spiped
	${INSTALL_DATA} ${WRKSRC}/COPYRIGHT ${PREFIX}/share/doc/spiped/
	${INSTALL_DATA} ${WRKSRC}/README ${PREFIX}/share/doc/spiped/
	${INSTALL_DATA} ${WRKSRC}/spipe/README ${PREFIX}/share/doc/spiped/README-spipe
	${INSTALL_DATA} ${WRKSRC}/spiped/README ${PREFIX}/share/doc/spiped/README-spiped
	perl -pi -e 's,/etc/ssh/spiped.key,${SYSCONFDIR}/spiped/spiped.key,' \
	    ${PREFIX}/share/doc/spiped/README

.include <bsd.port.mk>
