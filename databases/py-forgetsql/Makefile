# Created by: Anders Nordby <anders@FreeBSD.org>
# $FreeBSD$

PORTNAME=	forgetsql
PORTVERSION=	0.5.1
PORTREVISION=	2
CATEGORIES=	databases python
MASTER_SITES=	SF
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	forgetSQL-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Python module for object-oriented access to SQL databases

DEPRECATED=	Unmaintained, uses EOLed python27
EXPIRATION_DATE=	2020-01-27

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		python:2.7
USE_PYTHON=	distutils autoplist
NO_ARCH=	yes

PORTDOCS=	BUGS README TODO

OPTIONS_DEFINE=	DOCS MYSQL PGSQL

MYSQL_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}MySQLdb>=1.2.2:databases/py-MySQLdb@${PY_FLAVOR}
PGSQL_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2@${PY_FLAVOR}

.include <bsd.port.options.mk>

post-build:
	@cd ${WRKSRC}/lib && ${PYTHON_CMD} -c 'import forgetSQL'
	@cd ${WRKSRC}/lib && ${PYTHON_CMD} -O -c 'import forgetSQL'

post-install:
	${INSTALL_DATA} ${WRKSRC}/lib/forgetSQL.pyc ${STAGEDIR}${PYTHON_SITELIBDIR}/
	${INSTALL_DATA} ${WRKSRC}/lib/forgetSQL.pyo ${STAGEDIR}${PYTHON_SITELIBDIR}/
.if !${PORT_OPTIONS:MPGSQL} && !${PORT_OPTIONS:MMYSQL}
	@${ECHO}
	@${ECHO_MSG} "===> You did not set MYSQL or PGSQL. To make this port usable,"
	@${ECHO_MSG} "===> you should install py-psycopg or py-MySQLdb from ports/databases."
	@${ECHO}
.endif

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
.for f in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${f} ${STAGEDIR}${DOCSDIR}/
.endfor

.include <bsd.port.mk>
