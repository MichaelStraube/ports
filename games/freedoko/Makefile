PORTNAME=	freedoko
PORTVERSION=	0.8.0
PORTREVISION=	1
CATEGORIES=	games
MASTER_SITES=	SF/free-doko/source
DISTNAME=	FreeDoko_${PORTVERSION}.src

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Play the card game Doppelkopf
WWW=		https://free-doko.sourceforge.net/

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS+=	a2x:textproc/asciidoc w3m:www/w3m flip:textproc/flip \
		rsync:net/rsync
LIB_DEPENDS=	libharfbuzz.so:print/harfbuzz

USES=		gettext-runtime gettext-tools gmake gnome localbase \
		pkgconfig zip:infozip openal:al,alut tex
USE_GNOME=	gdkpixbuf2 gtkmm30
USE_TEX=	pdftex:build dvipsk:build

LDFLAGS_i386=	-Wl,-znotext

WRKSRC=		${WRKDIR}/${DISTNAME:R}
ALL_TARGET=	compile documentation

post-patch:
	@${REINPLACE_CMD} -e \
		's|-lstdc++fs|-lstdc++|g' \
		${WRKSRC}/src/Makefile

.include <bsd.port.mk>
