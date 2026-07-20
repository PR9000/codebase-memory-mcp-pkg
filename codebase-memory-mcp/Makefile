PORTNAME=		codebase-memory-mcp
DISTVERSION=		0.8.1.20260720
CATEGORIES=		devel

MAINTAINER=		pr9000@tutamail.com
COMMENT=		Fast code intelligence engine and MCP server for AI coding agents
WWW=			https://github.com/PR9000/codebase-memory-mcp

LICENSE=		MIT
LICENSE_FILE=		${WRKSRC}/LICENSE

USES=			compiler:c11 gmake

CONFLICTS_INSTALL=	codebase-memory-mcp-ui

USE_GITHUB=		yes
GH_ACCOUNT=		PR9000
GH_TAGNAME=		freebsd-ports

MAKEFILE=		Makefile.cbm
ALL_TARGET=		cbm
MAKE_ARGS=		CC="${CC}" CXX="${CXX}" HARDENING=1 CFLAGS="${CFLAGS} -DCBM_VERSION=\\\"${DISTVERSION}\\\""

PLIST_FILES=		bin/codebase-memory-mcp

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/build/c/codebase-memory-mcp ${STAGEDIR}${PREFIX}/bin/codebase-memory-mcp

do-test:
	@cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} ${MAKE_CMD} -f Makefile.cbm test

.include <bsd.port.mk>
