# $FreeBSD$

PORTNAME=	xf86-video-qxl
DISTVERSION=	0.1.5
PORTREVISION=	1
CATEGORIES=	x11-drivers

MAINTAINER=	ports@FreeBSD.org
COMMENT=	X.Org X server -- QXL display driver

LICENSE=	MIT

BUILD_DEPENDS=	spice-protocol>=0.12.10:devel/spice-protocol \
		${LOCALBASE}/include/linux/input.h:multimedia/v4l_compat
LIB_DEPENDS=	libspice-server.so:devel/libspice-server

USES=		localbase:ldflags pkgconfig python:2.7 shebangfix

USE_XORG=	xfont
XORG_CAT=	driver

CONFIGURE_ARGS+=--enable-xspice

python_OLD_CMD=	"/usr/bin/python"
SHEBANG_FILES=	scripts/Xspice

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/X11/xorg.conf.d
	${INSTALL_DATA} ${WRKSRC}/examples/spiceqxl.xorg.conf.example \
		${STAGEDIR}${PREFIX}/etc/X11/xorg.conf.d/spiceqxl.xorg.conf.example

.include <bsd.port.mk>
