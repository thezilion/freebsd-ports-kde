# $FreeBSD$

PORTNAME=	plasma-scriptengine-python
PORTVERSION=	${KDE4_WORKSPACE_VERSION}
PORTREVISION=	1
CATEGORIES=	x11 kde kde-applications
DISTNAME=	kde-workspace-${PORTVERSION}

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Plasma scriptengine for Python

NO_ARCH=	yes
USES=		cmake:outsource kde:4 python:2 tar:xz
USE_KDE=	kdelibs pykde4 automoc4
USE_QT4=	qmake_build moc_build uic_build rcc_build
DISTINFO_FILE=	${.CURDIR:H:H}/x11/kde4-workspace/distinfo

KDE_APPLICATIONS_VERSION=	15.08.0

CMAKE_SOURCE_PATH=	${WRKSRC}/plasma/generic/scriptengines/python

pre-configure:
	${REINPLACE_CMD} -e 's,$${PYTHON_SITE_PACKAGES_DIR},${PYTHONPREFIX_SITELIBDIR},g' \
		${CMAKE_SOURCE_PATH}/CMakeLists.txt

.include <bsd.port.mk>
