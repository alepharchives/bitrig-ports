# $OpenBSD: Makefile,v 1.4 2012/10/18 21:23:51 espie Exp $

COMMENT=	expose media content over D-Bus for Rygel to consume

GNOME_PROJECT=	grilo-mediaserver2
GNOME_VERSION=	0.0.2
# git clone of 4614b1969dcdea2c254af3178b70966282468c07

SHARED_LIBS +=  mediaserver2              0.0 # 0.0

CATEGORIES+=	multimedia

HOMEPAGE=	http://live.gnome.org/Grilo

# LGPLv2.1
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=	Yes

MODULES=	devel/gettext \
		x11/gnome

WANTLIB += c dbus-1 dbus-glib-1 ffi gio-2.0 glib-2.0 gmodule-2.0
WANTLIB += gobject-2.0 grilo-0.2 gthread-2.0 m pcre pthread xml2
WANTLIB += z

LIB_DEPENDS=	x11/gnome/grilo \
		x11/dbus-glib

MAKE_FLAGS=	bin_PROGRAMS="grilo-ms2"
FAKE_FLAGS=	sysconfdir="${PREFIX}/share/examples/grilo-mediaserver2/"

############################################################
# XXX: Remove the following when updating to a real release.
MASTER_SITES=	http://distfiles.nl/

AUTOCONF_VERSION=	2.68
AUTOMAKE_VERSION=	1.11

BUILD_DEPENDS +=x11/gnome/common \
		devel/autoconf/${AUTOCONF_VERSION} \
		devel/automake/${AUTOMAKE_VERSION} \
		devel/libtool

do-configure:
	@cd ${WRKSRC} && \
		AUTOCONF_VERSION=${AUTOCONF_VERSION} \
		AUTOMAKE_VERSION=${AUTOMAKE_VERSION} \
		env ${CONFIGURE_ENV} \
		./autogen.sh ${CONFIGURE_ARGS} \
			--disable-maintainer-mode \
			--disable-silent-rules
############################################################

.include <bsd.port.mk>
