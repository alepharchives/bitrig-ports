# $OpenBSD: Makefile,v 1.39 2012/11/22 17:37:35 ajacoutot Exp $

COMMENT=	framework for granting privileged operations to users

DISTNAME=	polkit-0.108
REVISION=	0

SHARED_LIBS +=  polkit-gobject-1	2.0 # .0.0
SHARED_LIBS +=  polkit-agent-1		2.0 # .0.0

CATEGORIES=	sysutils security

HOMEPAGE=	http://www.freedesktop.org/wiki/Software/polkit

MAINTAINER=	Antoine Jacoutot <ajacoutot@openbsd.org>

# GPLv2+
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes

WANTLIB += c expat gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0 pthread

MASTER_SITES=	http://www.freedesktop.org/software/polkit/releases/

MODULES=	textproc/intltool \
		lang/python

BUILD_DEPENDS=	${MODGNU_AUTOMAKE_DEPENDS} \
		${MODGNU_AUTOCONF_DEPENDS} \
		devel/gettext \
		devel/gobject-introspection \
		devel/spidermonkey

RUN_DEPENDS=	x11/dbus

# dlopen() libmozjs185.so
RUN_DEPENDS +=	devel/spidermonkey

USE_LIBTOOL=	Yes
# needs AM_PROG_LIBTOOL
BUILD_DEPENDS+=	devel/libtool

# We do no want to depends on gtk-doc as it creates a dependency loop:
# polkit -> gtk-doc -> yelp -> gconf2 -> polkit
BUILD_DEPENDS+=	textproc/docbook-xsl

LIB_DEPENDS=	devel/glib2

AUTOCONF_VERSION= 2.68
AUTOMAKE_VERSION=1.10

MODGNU_CONFIG_GUESS_DIRS= ${WRKSRC} ${WRKSRC}/test/mocklibc

CONFIGURE_STYLE= gnu
CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib"
CONFIGURE_ARGS=	${CONFIGURE_SHARED} \
		--disable-gtk-doc \
		--disable-libsystemd-login \
		--mandir=${PREFIX}/man \
		--enable-introspection \
		--enable-man-pages \
		--enable-examples \
		--with-os-type=openbsd \
		--with-authfw=bsdauth \
		--with-polkitd-user=_polkitd

# If one of these tools is found at configure stage, it might be used,
# no matter whether we use --disable-gtk-doc or not.
CONFIGURE_ENV +=ac_cv_path_GTKDOC_CHECK="" \
		ac_cv_path_GTKDOC_REBASE="" \
		ac_cv_path_GTKDOC_MKPDF=""

MODPY_BUILDDEP=	No
MODPY_RUNDEP=	No
USE_GMAKE=	Yes
USE_GROFF=	Yes

FAKE_FLAGS=	sysconfdir=${PREFIX}/share/examples/polkit

pre-configure:
	${SUBST_CMD} ${WRKSRC}/docs/man/pkexec.xml \
		${WRKSRC}/docs/man/polkit.xml \
		${WRKSRC}/docs/extensiondir.xml \
		${WRKSRC}/src/examples/org.freedesktop.policykit.examples.pkexec.policy.in
	cd ${WRKSRC} && \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} \
		AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		${LOCALBASE}/bin/autoreconf

.include <bsd.port.mk>
