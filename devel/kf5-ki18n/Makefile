# $FreeBSD$

PORTNAME=	ki18n
DISTVERSION=	${KDE_FRAMEWORKS_VERSION}
CATEGORIES=	devel kde kde-frameworks

MAINTAINER=	kde@FreeBSD.org
COMMENT=	KF5 advanced internationalization framework

USES=		cmake:outsource compiler:c++11-lib gettext-runtime \
		gettext-tools:build,run kde:5 qt:5 tar:xz
USE_KDE=	ecm
USE_QT=		buildtools_build concurrent core qmake_build qml script testlib

.include <bsd.port.mk>
