# $OpenBSD: Makefile,v 1.1.1.1 2012/06/07 12:06:47 jasper Exp $

COMMENT=	GNU standards-compliant Makefile generator

VERSION=	1.12
DISTNAME=	automake-${VERSION}
PKGSPEC=	automake->=${VERSION},<1.13

CATEGORIES=	devel
MASTER_SITES=	${MASTER_SITE_GNU:=automake/}

HOMEPAGE=	http://www.gnu.org/software/automake/

# GPLv2
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MODULES=		lang/python

MODPY_BUILDDEP=		No
MODPY_RUNDEP=		No

AUTOCONF_VERSION=	2.68

BUILD_DEPENDS =		${RUN_DEPENDS}
RUN_DEPENDS=		${MODGNU_AUTOCONF_DEPENDS}

SUFFIX=			-${VERSION}
CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS=		--infodir=${PREFIX}/info
CONFIGURE_ENV +=	AUTOCONF_VERSION=${AUTOCONF_VERSION}

MAKE_FLAGS+=		pkgvdatadir=${PREFIX}/share/automake${SUFFIX} \
			APIVERSION=${VERSION}
SUBST_VARS=		SUFFIX

FAKE_FLAGS=		docdir=${PREFIX}/share/doc/automake${SUFFIX}

REGRESS_DEPENDS=	${BASE_PKGPATH} \
			${MODPY_RUN_DEPENDS} \
			devel/libtool \
			devel/gmake \
			archivers/bzip2 \
			devel/bison \
			editors/emacs21 \
			devel/dejagnu

REGRESS_ENV=		AUTOCONF_VERSION=${AUTOCONF_VERSION} \
			MAKE=${GMAKE}

do-regress:
	    ln -sf ${MODPY_BIN} ${WRKDIR}/bin/python
	    @cd ${WRKBUILD} && \
	    	exec ${SETENV} ${MAKE_ENV} ${REGRESS_ENV} \
		    ${MAKE_PROGRAM} ${ALL_REGRESS_FLAGS} \
		    -f ${MAKE_FILE} ${REGRESS_TARGET}

pre-configure:
	${SUBST_CMD} ${WRKSRC}/doc/automake.texi

post-install:
	cd ${PREFIX}/info && mv automake.info automake${SUFFIX}.info
	perl -pi -e "s,automake\: \(automake\),automake-1\.12\: \(automake-1\.12\)," \
		${PREFIX}/info/automake${SUFFIX}.info
	perl -pi -e "s,aclocal\: \(automake\),aclocal: \(automake-1\.12\)," \
		${PREFIX}/info/automake${SUFFIX}.info

.for f in info-1 info-2 info-3
	cd ${PREFIX}/info && mv automake.${f} automake${SUFFIX}.${f} \
		&& perl -pi -e "s,automake.${f},automake${SUFFIX}.${f}," \
		${PREFIX}/info/automake${SUFFIX}.info
.endfor

.include <bsd.port.mk>