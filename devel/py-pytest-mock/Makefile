# $FreeBSD$

PORTNAME=	pytest-mock
PORTVERSION=	1.6.0
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	olgeni@FreeBSD.org
COMMENT=	Thin wrapper around the mock package for easier use with py.test

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}setuptools_scm>=0:devel/py${SLAVE_SUFFIX}-setuptools_scm
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}mock>0:devel/py-mock

NO_ARCH=	yes
USES+=		python
USE_PYTHON=	autoplist concurrent distutils

do-test:
	@cd ${WRKSRC} && ${PYTHON_CMD} -m pytest

.include <bsd.port.mk>
