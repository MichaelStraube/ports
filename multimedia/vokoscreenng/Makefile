PORTNAME=	vokoscreenng
DISTVERSION=	4.0.0
CATEGORIES=	multimedia

MAINTAINER=	michael.straubej@gmail.com
COMMENT=	Easy to use screencast creator
WWW=		https://linuxecke.volkoh.de/vokoscreen/vokoscreen.html

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/../COPYING

LIB_DEPENDS=	libwayland-client.so:graphics/wayland libpulse.so:audio/pulseaudio

USES=		qt:6 qmake gstreamer pkgconfig gnome xorg
USE_QT=		base multimedia translations
USE_GSTREAMER=	good bad ugly libav pulse
USE_GNOME=	glib20
USE_XORG=	x11

USE_GITHUB=	yes
GH_ACCOUNT=	vkohaupt
GH_PROJECT=	vokoscreenNG

WRKSRC_SUBDIR=	src

post-patch:
	# These substitutions can be removed for upstream releases > 4.0.0
	${SED} -i -e 's|linux:|unix:|g' ${WRKSRC}/QGlobalShortcut/qglobalshortcut.pri
	${FIND} ${WRKSRC} -type f -exec  ${SED} -i -e 's|Q_OS_LINUX|Q_OS_UNIX|g' {} +

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/vokoscreenNG \
		${STAGEDIR}${PREFIX}/bin

	${INSTALL_DATA} ${WRKSRC}/applications/vokoscreenNG.desktop \
		${STAGEDIR}${PREFIX}/share/applications

	${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/256x256/apps
	${INSTALL_DATA} ${WRKSRC}/applications/vokoscreenNG.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/256x256/apps

.include <bsd.port.mk>
