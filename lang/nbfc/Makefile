# $OpenBSD

COMMENT =		new brainfuck compiler

DISTNAME =		nbfc-0.1
REVISION =		0

CATEGORIES =		lang

HOMEPAGE =		http://koeln.ccc.de/ablage/brainfuck/

MAINTAINER =		Pascal Stumpf <Pascal.Stumpf@cubes.de>

# BSD
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

WANTLIB =		c

MASTER_SITES =		${HOMEPAGE}

USE_GROFF =		Yes

NO_REGRESS =		Yes

SUBST_VARS +=		CC CFLAGS

post-patch:
	@perl -pi -e 's,bison -y,yacc -,g;' \
		-e 's,gcc,\$${CC} \$${CFLAGS},g' ${WRKSRC}/Makefile

pre-configure:
	${SUBST_CMD} ${WRKSRC}/config.h

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/nbfc ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/nbfc.1 ${PREFIX}/man/man1

.include <bsd.port.mk>
