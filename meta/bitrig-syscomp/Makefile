COMMENT=	System Compiler Meta Package

PKGNAME=	bitrig-syscomp-1.0
REVISION=	21

MAINTAINER=	Marco Peereboom <marco@bitrig.org>

BUILD_DEPENDS=	bitrig/bitrig-binutils \
		bitrig/bitrig-gcc,-gcclibs \
		bitrig/bitrig-gcc,-main \
		bitrig/bitrig-llvm \
		bitrig/bitrig-gdb \
		devel/git \
		sysutils/cdrtools \
		archivers/libarchive

RUN_DEPENDS = ${BUILD_DEPENDS}

.include <bsd.port.mk>
