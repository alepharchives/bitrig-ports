# $OpenBSD: Makefile,v 1.27 2012/10/12 09:46:46 kirby Exp $

COMMENT-main =	flexible network host monitoring, client
COMMENT-server =flexible network host monitoring, server

V =		2.0.7
DISTNAME =	munin-$V
PKGNAME-main =	munin-node-$V
PKGNAME-server =munin-server-$V
CATEGORIES =	net

HOMEPAGE =	http://munin-monitoring.org/
MASTER_SITES =	${MASTER_SITE_SOURCEFORGE:=munin/}

# Mostly GPLv2. VeraMono.ttf has a non-restrictive license (copyright notice
# embedded in the font or xenocara/font/bitstream-vera-ttf/COPYRIGHT.TXT).
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MAINTAINER =		Stuart Henderson <sthen@openbsd.org>

MULTI_PACKAGES =	-main -server

# Used for file locations and MODPY_BIN, RUBY, MODRUBY_ADJ_FILES.
# Only very minor optional munin plugins use these languages so they
# aren't forced as dependencies (same for bash).
MODULES =		lang/python lang/ruby
# No need for MODx_RUNDEP as we already override RUN_DEPENDS-{main,server}
MODPY_BUILDDEP =	No
MODRUBY_BUILDDEP =	No
MODRUBY_REV =		1.9

RUN_DEPENDS-main =	logtail-*|logsentry-*:sysutils/logtail \
			devel/p5-Log-Log4perl \
			devel/p5-Net-Server \
			net/p5-Net-CIDR
RUN_DEPENDS-server +=	converters/p5-DateManip \
			devel/p5-File-Copy-Recursive \
			net/p5-IO-Socket-INET6 \
			net/rrdtool,-perl \
			www/fcgi \
			www/p5-HTML-Template \
			www/p5-URI \
			net/munin,-main

USE_GMAKE =		Yes
ALL_TARGET =		default build-doc build-man
WRKDIST =		${WRKDIR}/${DISTNAME:S/_/-/}
PKG_ARCH =		*

CONFIGURE_STYLE =	none # hack, otherwise python.port.mk overrides target

MAKE_ENV +=		CONFDIR=${SYSCONFDIR}/munin \
			OSTYPE=openbsd \
			PREFIX=${PREFIX} \
			PYTHON=${MODPY_BIN}
MAKE_FLAGS +=		BASH=${LOCALBASE}/bin/bash

FAKE_FLAGS +=		HTMLDIR=${WRKINST}/${PREFIX}/share/examples/munin/www \
			CGIDIR=${WRKINST}/${PREFIX}/share/examples/munin/www \
			DOCDIR=${WRKINST}/${PREFIX}/share/doc/munin \
			CONFDIR=${WRKINST}/${PREFIX}/share/examples/munin

MUNIN_PLUGINS =		bgpd if_pps_ intr pf_changes pf_searches pf_states \
			sensors_ vmstat

.for i in ${MUNIN_PLUGINS}
SUBST_LIST += ${FILESDIR}/$i ${WRKSRC}/plugins/node.d.openbsd/$i.in
.endfor

post-extract:
	cp -Rp ${WRKSRC}/plugins/node.d.freebsd ${WRKSRC}/plugins/node.d.openbsd
	${SUBST_CMD} -c ${SUBST_LIST}
	chmod -R +x ${WRKSRC}/plugins/node.d.openbsd
	rm ${WRKSRC}/plugins/node.d.openbsd/memory.in # not yet ported
	rm ${WRKSRC}/plugins/node.d.openbsd/uptime.in # OpenBSD incompatible

# Fixup hardcoded paths in plugins to use TRUEPREFIX/LOCALBASE as appropriate,
# there are far too many to handle this via patches/SUBST_CMD, and this method
# plays nicer with update-patches.
pre-configure:
	cd ${WRKSRC}/node/sbin; \
	${SUBST_CMD} munin-node munin-node-configure munin-run; \
	rm munin-{node,node-configure,run}.{beforesubst,orig}; \
	perl -pi -e 's,/etc/munin/plugins,${SYSCONFDIR}/munin/plugins,g;' \
	    -e 's,/etc/munin/node.d,${SYSCONFDIR}/munin/plugins,g;' \
	    -e 's,/usr/local/libexec/munin,${TRUEPREFIX}/libexec/munin,g;' \
	    -e 's,/usr/local,${LOCALBASE},g;' \
	    -e 's,/usr/share/munin/node/plugins-auto,${TRUEPREFIX}/libexec/munin/plugins,g;' \
	    ${WRKSRC}/plugins/node.d/* ${WRKSRC}/plugins/node.d.openbsd/*

post-install:
	${MODRUBY_RUBY_ADJ} ${PREFIX}/libexec/munin/plugins/tomcat_
	${INSTALL_DATA} ${FILESDIR}/openbsd-packages \
	    ${PREFIX}/share/examples/munin/plugin-conf.d
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/munin/
	${INSTALL_DATA} ${WRKSRC}/UPGRADING ${PREFIX}/share/doc/munin/
	@touch ${PREFIX}/share/examples/munin/munin-cgi-graph.log
	@touch ${PREFIX}/share/examples/munin/munin-cgi-html.log
	@rm ${PREFIX}/man/man8/munin-graph.8 # no data in it

.include <bsd.port.mk>
