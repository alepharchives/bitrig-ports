# $OpenBSD: Makefile,v 1.22 2012/11/10 15:01:15 stsp Exp $

COMMENT =		canvas API for X
VERSION = 		1.7.1
DISTNAME =		evas-${VERSION}
EPOCH =			2

SHARED_LIBS +=  evas                 2.0      # 8.1

# BSD
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

USE_LIBTOOL =		Yes

WANTLIB += GL X11 Xdamage Xext Xfixes Xrender Xxf86vm crypto drm
WANTLIB += eet eina expat ffi fontconfig freetype fribidi gif
WANTLIB += glib-2.0 gobject-2.0 gthread-2.0 harfbuzz icudata icule
WANTLIB += icuuc jpeg m pcre png pthread ssl stdc++ tiff xcb z

MODULES=		devel/gettext

VMEM_WARNING =	Yes

LIB_DEPENDS =		x11/e17/eet>=2.0 \
			graphics/libungif \
			graphics/png \
			graphics/tiff \
			graphics/jpeg \
			graphics/libungif \
			devel/harfbuzz \
			devel/glib2 \
			devel/fribidi \
			devel/libffi

CONFIGURE_ARGS +=	--disable-doc \
			--enable-no-dither-mask \
			--enable-small-dither-mask \
			--enable-line-dither-mask \
			--enable-word-cache \
			--enable-metric-cache \
			--disable-wayland-shm \
			--disable-wayland-egl

# ARGB Conversion from 32 to other pixel depths (slower -> faster)(nice -> ugly)
#			--enable-small-dither-mask
#			--enable-line-dither-mask
#			--enable-no-dither-mask
# Experimental performance
#	Enable experimental word caching to speed up rendering [[default=disabled]]
#			--enable-word-cache
#	Enable experimental metric caching to speed up rendering [[default=disabled]]
#			--enable-metric-cache
# performance
#			--disable-evas-magic-debug
# performance multi CPU / rthread needed (attach thread to CPU, pipe rendering)
#			--enable-pipe-render
#			--enable-async-render
# performance / cahing, activate by user, need shm_open() ! (fix with shm_get() ?)
#			--enable-evas-cserve
# engine modules : for performance, static ?
#	software
#			--enable-software-xlib: libx11 (http://xorg.freedesktop.org/)
#			--enable-software-xcb: libxcb (http://xorg.freedesktop.org/)
#			--enable-software-8-x11
#			--enable-software-16-x11: libxrender (http://xorg.freedesktop.org/)
#	xrender x11 : libxrender (http://xorg.freedesktop.org/)
#			--enable-xrender-x11
#			--enable-xrender-xcb
#	gl x11 engine : libxrender (http://xorg.freedesktop.org/)
#			--enable-gl-x11
#	gl engine flavor (active gles + choose one of variety)
#			--enable-gl-flavor-gles
#			--enable-gles-variety-sgx (Most GL-ES2 GPUs with shader compiler)
#			--enable-gles-variety-s3c6410 (s3c6410 with offline shader compiler)

CONFIGURE_ENV +=	CXXFLAGS="${CFLAGS} -I${LOCALBASE}/include -I${X11BASE}/include" \
			CPPFLAGS="${CFLAGS} -I${LOCALBASE}/include -I${X11BASE}/include" \
			CFLAGS="${CFLAGS} -I${LOCALBASE}/include -I${X11BASE}/include" \
			LDFLAGS="${LDFLAGS} -L${LOCALBASE}/lib -L${X11BASE}/lib"

FULLARCH =		${MACHINE_ARCH:S/amd64/x86_64/}
SUBST_VARS +=		FULLARCH OSREV VERSION

.include <bsd.port.mk>
