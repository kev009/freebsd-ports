# $FreeBSD$

PORTNAME=	cryptominisat
DISTVERSION=	5.6.3
PORTREVISION=	1
CATEGORIES=	math

MAINTAINER=	arrowd@FreeBSD.org
COMMENT=	General-purpose award-winning SAT solver

LICENSE=	MIT LGPL21
LICENSE_COMB=	multi
LICENSE_FILE_LGPL21=	${WRKSRC}/LICENSE.txt
LICENSE_FILE_MIT=	${WRKSRC}/LICENSE.txt

BROKEN_powerpc64=	fails to compile: main.cpp: undefined reference to boost::program_options::abstract_variables_map::operator[]

LIB_DEPENDS=	libboost_program_options.so:devel/boost-libs

USES=		cmake:outsource compiler:c++11-lib
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	msoos

CMAKE_ON=	NOM4RI
CMAKE_OFF=	ENABLE_PYTHON_INTERFACE

.include <bsd.port.mk>
