# $OpenBSD: Makefile,v 1.3 2012/11/06 11:48:28 dcoppa Exp $

COMMENT=	Universal Plug and Play SDK

DISTNAME=	libupnp-1.6.17
EXTRACT_SUFX=	.tar.bz2

CATEGORIES=	net devel

SHARED_LIBS +=  ixml                         0.1 # .2.7
SHARED_LIBS +=  threadutil                   1.0 # .6.2
SHARED_LIBS +=  upnp                         1.0 # .9.1

HOMEPAGE=	http://pupnp.sourceforge.net/

# BSD
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=pupnp/}

WANTLIB =	pthread

USE_LIBTOOL=	Yes

CONFIGURE_STYLE= gnu
MODGNU_CONFIG_GUESS_DIRS=${WRKSRC}/build-aux
# HAVE_COMPAT does not do anything
CONFIGURE_ENV=	ac_cv_cflags_gcc_option__Os=no \
		ac_cv_lib_compat_ftime=no

.ifdef DEBUG
CONFIGURE_ARGS+= --enable-debug
.endif

.include <bsd.port.mk>
