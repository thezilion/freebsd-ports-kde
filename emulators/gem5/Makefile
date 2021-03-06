# Created by: Veniamin Gvozdikov <vg@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gem5
PORTVERSION=	0.0.${DATE}
CATEGORIES=	emulators

MAINTAINER=	vg@FreeBSD.org
COMMENT=	gem5 Simulator System

BUILD_DEPENDS=	swig2.0:devel/swig20 \
		scons:devel/scons

BROKEN_armv6=		fails to link: undefined reference to HDLcd::BUS_OPTIONS_RESETV
BROKEN_i386=		does not build
BROKEN_mips64=		fails to build: claims that gcc version 4.6 or newer required
BROKEN_powerpc64=	fails to build: claims that gcc version 4.6 or newer required

DATE=		20140422
USE_GITHUB=	yes
GH_ACCOUNT=	CTSRD-CHERI
GH_TAGNAME=	99d65cc
SWIG_BIN=	swig2.0
USES=		gmake

.include <bsd.port.pre.mk>

post-patch:
	@${REINPLACE_CMD} -e 's|sys/termios.h|termios.h|' \
		${WRKSRC}/src/base/vnc/vncserver.cc \
		${WRKSRC}/src/dev/terminal.cc \
		${WRKSRC}/util/term/term.c

do-build:
	cd ${WRKSRC} && ${GMAKE} -C util/term
	cd ${WRKSRC} && ${SETENV} SWIG="${PREFIX}/bin/${SWIG_BIN}" scons \
		build/ARM/gem5.opt

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${PORTNAME} \
		${STAGEDIR}${PREFIX}/${PORTNAME}/ARM
	(cd ${WRKSRC} && ${COPYTREE_SHARE} configs \
		${STAGEDIR}${PREFIX}/${PORTNAME})
	(cd ${WRKSRC} && ${INSTALL_PROGRAM} build/ARM/gem5.opt \
		${STAGEDIR}${PREFIX}/${PORTNAME}/ARM/gem5.opt)
	(cd ${WRKSRC} && ${INSTALL_PROGRAM} util/term/m5term \
		${STAGEDIR}${PREFIX}/bin/m5term)

.include <bsd.port.post.mk>
