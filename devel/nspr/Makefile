# $OpenBSD: Makefile,v 1.44 2012/11/12 20:39:09 landry Exp $

ONLY_FOR_ARCHS=	alpha amd64 arm i386 mips64 mips64el powerpc sparc sparc64 hppa

COMMENT =		Netscape Portable Runtime

VER=			4.9.3
DISTNAME=		nspr-${VER}

SO_VERSION=		22.2
.for _lib in nspr4 plc4 plds4
SHARED_LIBS+=		${_lib} ${SO_VERSION}
.endfor

CATEGORIES=		devel

HOMEPAGE=		http://www.mozilla.org/projects/nspr/index.html

MAINTAINER=		Landry Breuil <landry@openbsd.org>

WANTLIB=		c pthread

# MPL - Mozilla Public License
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MASTER_SITES=		http://ftp.eu.mozilla.org/pub/mozilla.org/nspr/releases/v${VER}/src/ \
			http://ftp.mozilla.org/pub/mozilla.org/nspr/releases/v${VER}/src/

USE_GMAKE=		Yes
AUTOCONF_VERSION=	2.13
CONFIGURE_STYLE=	autoconf no-autoheader
CONFIGURE_ARGS+=	--disable-debug \
			--with-pthreads

MAKE_ENV=		SO_VERSION="${SO_VERSION}"
CONFIGURE_ENV=		${MAKE_ENV}

WRKSRC=			${WRKDIST}/mozilla/nsprpub
MODGNU_CONFIG_GUESS_DIRS=${WRKSRC}/build/autoconf

do-regress:
	${MAKE_PROGRAM} -C ${WRKSRC}/pr/tests
	${MAKE_PROGRAM} -C ${WRKSRC}/lib/tests
	@cd ${WRKSRC}/pr/tests && ulimit -Sn 192 && env TZ=gmt \
		LD_LIBRARY_PATH=${WRKSRC}/dist/lib /bin/ksh runtests.sh
	LD_LIBRARY_PATH=${WRKSRC}/dist/lib ${WRKSRC}/lib/tests/string
	LD_LIBRARY_PATH=${WRKSRC}/dist/lib ${WRKSRC}/lib/tests/base64t

.include <bsd.port.mk>
