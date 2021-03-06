# Created by: Thomas Gellekum <tg@FreeBSD.org>
# $FreeBSD$

PORTNAME=	qcad
PORTVERSION=	3.21.1.1
DISTVERSIONPREFIX=	v
PORTREVISION=	2
CATEGORIES=	cad
DIST_SUBDIR=	${PORTNAME}

MAINTAINER=	mr@FreeBSD.org
COMMENT=	Professional CAD system

LICENSE=	GPLv3

BUILD_DEPENDS=	bash:shells/bash	\
		${LOCALBASE}/lib/libopenNURBS.a:graphics/opennurbs
LIB_DEPENDS=	libquazip5.so:archivers/quazip@qt5

MAKE_JOBS_UNSAFE=yes

USES=		gmake qmake qt:5
USE_GITHUB=	yes
USE_LDCONFIG=	yes
USE_QT=		buildtools qmake_build \
		designer gui help imageformats network opengl script \
		scripttools sql svg uitools xml xmlpatterns webkit
USE_GL=		glu

DESKTOP_ENTRIES="QCad"	\
		"" \
		"${DATADIR}/scripts/qcad_icon.png"	\
		"${PREFIX}/bin/qcad-bin"	\
		""	\
		true

.if defined(WITH_DEBUG)
RESDIR=		${WRKSRC}/debug
.else
RESDIR=		${WRKSRC}/release
.endif

SHRLIBS=	qcadcore qcadecmaapi qcadentity qcadgrid qcadgui qcadoperations	\
		qcadsnap qcadspatialindex qcadstemmer spatialindexnavel qcadzip
STALIBS=	dxflib stemmer
SHRDIR=		fonts libraries linetypes patterns plugins scripts themes ts
#QSCRIPTS should not be installed to avoid conflicts with texlive-base
QSCRIPTS=	bbox dwg2bmp dwg2pdf dwg2svg

pre-configure:
	${REINPLACE_CMD} -e "s|%%DATADIR%%|${DATADIR}|"	\
		${WRKSRC}/src/core/RS.cpp
	${REINPLACE_CMD} -e "s|%%DATADIR%%|${DATADIR}|"	\
		${WRKSRC}/src/core/RSettings.cpp

do-install:
	${INSTALL_PROGRAM} ${RESDIR}/qcad-bin ${STAGEDIR}${PREFIX}/bin/
	${LN} -sf qcad-bin ${STAGEDIR}${PREFIX}/bin/qcad
.for lib in ${SHRLIBS:C|^|lib|:C|$|.so|}
	${INSTALL_LIB} ${RESDIR}/${lib} ${STAGEDIR}${PREFIX}/lib/${lib}.0
	${LN} -sf ${lib}.0 ${STAGEDIR}${PREFIX}/lib/${lib}
.endfor
.for lib in ${STALIBS:C|^|lib|:C|$|.a|}
	${INSTALL_DATA} ${RESDIR}/${lib} ${STAGEDIR}${PREFIX}/lib/
.endfor
	${MKDIR} ${STAGEDIR}${DATADIR}
.for dir in ${SHRDIR}
	cd ${WRKSRC} && ${COPYTREE_SHARE} ${dir} ${STAGEDIR}${DATADIR}
.endfor
	${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	cd ${WRKSRC}/examples && ${COPYTREE_SHARE} . ${STAGEDIR}${EXAMPLESDIR}

.include <bsd.port.mk>
