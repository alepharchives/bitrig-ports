# $OpenBSD: Makefile,v 1.24 2012/10/20 16:00:58 gsoares Exp $

COMMENT =	high-level Python web framework

MODPY_EGG_VERSION =	1.4.2
LNAME =			django
DISTNAME =		Django-${MODPY_EGG_VERSION}
PKGNAME =		py-${LNAME}-${MODPY_EGG_VERSION}
CATEGORIES =		www

HOMEPAGE =	http://www.djangoproject.com/

MAINTAINER =	Ryan Boggs <rmboggs@gmail.com>

# BSD License
PERMIT_PACKAGE_CDROM =		Yes
PERMIT_PACKAGE_FTP =		Yes
PERMIT_DISTFILES_CDROM =	Yes
PERMIT_DISTFILES_FTP =		Yes

MASTER_SITES =	${HOMEPAGE}/m/releases/${MODPY_EGG_VERSION:R}/

MODULES =	lang/python

SUBST_VARS +=	LNAME

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/${LNAME}
	cd ${WRKSRC}/docs && pax -rw * ${PREFIX}/share/doc/${LNAME}

do-regress:
	cd ${WRKSRC} && env LC_CTYPE=en_US.UTF-8 PYTHONPATH=. \
		${MODPY_BIN} tests/runtests.py --settings=test_sqlite

.include <bsd.port.mk>
