# $OpenBSD: Makefile,v 1.13 2012/10/18 20:04:58 sthen Exp $

COMMENT =	web UI for icinga
DISTNAME =	icinga-web-$V

MODULES=	lang/php

RUN_DEPENDS =	www/pear \
		lang/php/${MODPHP_VERSION},-gd \
		lang/php/${MODPHP_VERSION},-ldap \
		lang/php/${MODPHP_VERSION},-xsl \
		php-pdo_mysql-${MODPHP_VSPEC}|php-pdo_pgsql-${MODPHP_VSPEC}:lang/php/${MODPHP_VERSION},-pdo_mysql \
		net/icinga/core \
		net/icinga/core,-ido \
		shells/bash
# Optional php extensions: soap xmlrpc memcache

BUILD_DEPENDS=	${RUN_DEPENDS}

LOCALSTATEDIR =	${BASELOCALSTATEDIR}/icinga

CONFIGURE_STYLE = gnu
CONFIGURE_ENV +=  PHP="${MODPHP_BIN}"
CONFIGURE_ARGS += \
	--datarootdir=${PREFIX} \
	--sbindir=/var/www/cgi-bin/icinga \
	--with-web-apache-path=${PREFIX}/etc \
	--with-api-cmd-file=/var/icinga/rw/icinga.cmd \
	--with-web-user=www \
	--with-web-group=www \
	--with-bin-user=${SHAREOWN} \
	--with-bin-group=${SHAREGRP} \
	--with-db-socket=/var/run/mysql/mysql.sock \
	--with-icinga-bin=${LOCALBASE}/bin/icinga \
	--with-icinga-cfg=${BASESYSCONFDIR}/icinga/icinga.cfg \
	--with-icinga-objects-dir=${BASESYSCONFDIR}/icinga/objects
# override default ("localhost") to allow tcp connections; makes mysql easier
CONFIGURE_ARGS += \
	--with-api-host=127.0.0.1 \
	--with-db-host=127.0.0.1

NO_REGRESS =	Yes
NO_BUILD =	Yes

INSTALL_TARGET = install install-apache-config

PREFIX =	/var/www/icinga-web

pre-configure:
	@ln -s ${MODPHP_BIN} ${WRKDIR}/bin/php

post-configure:
	@find ${WRKSRC}/bin -name '*.sh' -print0 | xargs -0r \
		perl -pi -e 's,^#!/bin/bash,#!${LOCALBASE}/bin/bash,g'

pre-install:
	${INSTALL_DATA_DIR} ${WRKINST}/var/www/conf/modules.sample

post-install:
	find ${WRKINST} -name '*.orig' -print0 | xargs -0r rm
	cd ${WRKSRC}/etc/schema; pax -rw ./ ${PREFIX}/etc/schema/
	for i in ${PREFIX}/etc/conf.d/*xml; do mv $$i $$i.dist; done

.include <bsd.port.mk>
