# $FreeBSD$

PORTNAME=	django-redis
PORTVERSION=	4.11.0
CATEGORIES=	www databases
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}dj22-

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Full featured Redis cache/session backend for Django

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}django22>=1.11:www/py-django22@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}redis>=2.10.0:databases/py-redis@${PY_FLAVOR}
TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}fakeredis>=0:databases/py-fakeredis@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}hiredis>=0:databases/py-hiredis@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}mock>=0:devel/py-mock@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}msgpack>=0:devel/py-msgpack@${PY_FLAVOR}

USES=		python:3.5+
USE_PYTHON=	autoplist distutils

NO_ARCH=	yes

do-test:
	@cd ${WRKSRC}/tests && ${PYTHON_CMD} runtests.py

.include <bsd.port.mk>
