# $OpenBSD: Makefile,v 1.2 2010/10/24 21:15:37 ajacoutot Exp $

COMMENT=	animated autohiding applications launcher

DISTNAME=	yeahlaunch-0.2
CATEGORIES=	x11

HOMEPAGE=	http://phrat.de/yeahtools.html

MAINTAINER=	Scott Vokes <vokes.s@gmail.com>

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

WANTLIB=	X11 c

MASTER_SITES=	http://phrat.de/

NO_REGRESS=	Yes

do-build:
	${CC} ${CFLAGS} -I${X11BASE}/include -c -o \
		${WRKBUILD}/yeahlaunch.o ${WRKSRC}/yeahlaunch.c
	${CC} -L${X11BASE}/lib -lX11 -o \
		${WRKBUILD}/yeahlaunch ${WRKBUILD}/yeahlaunch.o

do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/yeahlaunch ${PREFIX}/bin
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/yeahlaunch
	${INSTALL_DATA} ${WRKSRC}/README ${PREFIX}/share/doc/yeahlaunch/

.include <bsd.port.mk>
