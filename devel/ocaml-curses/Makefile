# $OpenBSD: Makefile,v 1.1.1.1 2012/11/06 20:53:47 jasper Exp $

COMMENT=		curses / ncurses bindings for OCaml

DISTNAME=		ocaml-curses-1.0.3
CATEGORIES=		devel

HOMEPAGE=		http://www.nongnu.org/ocaml-tmk/

# LGPLv2.1
PERMIT_PACKAGE_CDROM=   Yes
PERMIT_PACKAGE_FTP=     Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=   Yes

MASTER_SITES=		http://download.savannah.gnu.org/releases/ocaml-tmk/

WANTLIB += ncurses

MODULES=		lang/ocaml

BUILD_DEPENDS=		sysutils/findlib

USE_GMAKE=		Yes

AUTOCONF_VERSION=	2.59
CONFIGURE_STYLE=	autoconf

REGRESS_TARGET=		test

ALL_TARGET =		htdoc all

.include <bsd.port.arch.mk>
.if ${PROPERTIES:Mocaml_native}
ALL_TARGET +=		opt
.endif

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/ocaml-curses
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/ocaml-curses/html
	${INSTALL_DATA} ${WRKDIST}/doc/curses/html/* \
		${PREFIX}/share/doc/ocaml-curses/html/
	${INSTALL_DATA} ${WRKDIST}/CHANGES \
		${PREFIX}/share/doc/ocaml-curses/

.include <bsd.port.mk>
