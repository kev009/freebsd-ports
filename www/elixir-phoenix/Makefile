# $FreeBSD$

PORTNAME=	phoenix
PORTVERSION=	1.3.3
DISTVERSIONPREFIX=	v
CATEGORIES=	www
PKGNAMEPREFIX=	elixir-

MAINTAINER=	erlang@FreeBSD.org
COMMENT=	Web framework for Elixir

LICENSE=	MIT

USES=		elixir
USE_GITHUB=	yes
GH_ACCOUNT=	phoenixframework

OPTIONS_DEFINE=	COWBOY
COWBOY_DESC=	Use Cowboy library

COWBOY_BUILD_DEPENDS=	erlang-cowboy>=0:www/erlang-cowboy
COWBOY_RUN_DEPENDS=	erlang-cowboy>=0:www/erlang-cowboy

.include <bsd.port.options.mk>

MIX_BUILD_DEPS=	devel/elixir-plug \
		devel/elixir-poison \
		www/elixir-phoenix_pubsub
MIX_RUN_DEPS:=	${MIX_BUILD_DEPS}
MIX_EXTRA_APPS=	installer
MIX_EXTRA_DIRS=	installer/lib installer/templates
MIX_REWRITE=	yes

.include <bsd.port.mk>
