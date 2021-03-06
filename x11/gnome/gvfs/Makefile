# $OpenBSD: Makefile,v 1.82 2012/11/12 18:01:10 ajacoutot Exp $

COMMENT-main=	GNOME Virtual File System
COMMENT-smb=	samba module for GVFS

GNOME_PROJECT=	gvfs
GNOME_VERSION=	1.14.2

PKGNAME-main=	${DISTNAME}
PKGNAME-smb=	${GNOME_PROJECT}-smb-${GNOME_VERSION}

SHARED_LIBS +=  gvfscommon           4.0      # .0.0

# LGPLv2
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MODULES=	devel/gettext \
		x11/gnome \
		devel/dconf

WANTLIB += c ffi gcrypt gio-2.0 glib-2.0 gmodule-2.0 gobject-2.0 gpg-error
WANTLIB += gthread-2.0 pcre pthread secret-1 util z

WANTLIB-main +=	${WANTLIB}
WANTLIB-main += GL ICE SM X11 Xau Xcomposite Xcursor Xdamage Xdmcp
WANTLIB-main += Xext Xfixes Xi Xinerama Xrandr Xrender Xxf86vm archive
WANTLIB-main += atk-1.0 atk-bridge-2.0 atspi avahi-client avahi-common
WANTLIB-main += avahi-glib bz2 cairo cairo-gobject dbus-1 drm expat
WANTLIB-main += fontconfig freetype gdk-3 gdk_pixbuf-2.0 gnome-keyring
WANTLIB-main += gtk-3 harfbuzz icudata icule icuuc lzma m pango-1.0
WANTLIB-main += pangocairo-1.0 pangoft2-1.0 pixman-1 png pthread-stubs
WANTLIB-main += soup-2.4 soup-gnome-2.4 sqlite3 stdc++ xcb xcb-render
WANTLIB-main += xcb-shm xml2

WANTLIB-smb += ${WANTLIB}
WANTLIB-smb += gvfscommon smbclient execinfo talloc tdb wbclient

MODGNOME_DESKTOP_FILE=	Yes

# man pages
BUILD_DEPENDS += textproc/docbook-xsl

LIB_DEPENDS=	x11/gnome/libsecret

LIB_DEPENDS-main= ${LIB_DEPENDS} \
		archivers/libarchive \
		devel/libsoup,-gnome \
		net/avahi \
		x11/gtk+3

RUN_DEPENDS-smb= ${MODGETTEXT_RUN_DEPENDS}
LIB_DEPENDS-smb= ${LIB_DEPENDS} \
		${BASE_PKGPATH},-main=${GNOME_VERSION} \
		net/samba

CONFIGURE_ARGS=	--disable-cdda \
		--disable-bluray \
		--disable-fuse \
		--disable-hal \
		--disable-afc \
		--disable-obexftp \
		--disable-gphoto2 \
		--disable-gudev \
		--disable-udev \
		--disable-gdu

MULTI_PACKAGES=		-main
PSEUDO_FLAVORS=		no_smb
FLAVOR?=

.if ${FLAVOR:L:Mno_smb}
CONFIGURE_ARGS+= --disable-samba
.else
CONFIGURE_ARGS+= --enable-samba
MULTI_PACKAGES+= -smb
.endif

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/applications/
	${SUBST_CMD} -o ${SHAREOWN} -g ${SHAREGRP} \
		-c ${FILESDIR}/mount-archive.desktop.in \
		${PREFIX}/share/applications/mount-archive.desktop
	rm ${PREFIX}/lib/gio/modules/*.{a,la}

.include <bsd.port.mk>
