# $OpenBSD: Makefile,v 1.15 2019/11/10 19:56:58 ajacoutot Exp $

COMMENT=	template rendering and notifications with Consul

# XXX cannot update
# https://github.com/hashicorp/consul-template/issues/1307
GH_TAGNAME=	v0.20.1
GH_ACCOUNT=	hashicorp
GH_PROJECT=	consul-template

CATEGORIES=	sysutils net

HOMEPAGE=	https://www.consul.io/

MAINTAINER=	Antoine Jacoutot <ajacoutot@openbsd.org>

# MPLv2.0
PERMIT_PACKAGE=	Yes

WANTLIB += c pthread

MODULES=	lang/go
TEST_DEPENDS=	sysutils/consul

#MASTER_SITES=	https://distfiles.bsdfrog.org/

# creating a new distfile (needs devel/git, sysutils/dep)
# =======================
# mkdir -p ${HOME}/go/src/github.com/hashicorp/
# cd ${HOME}/go/src/github.com/hashicorp/
# git clone https://github.com/hashicorp/consul-template.git
# cd consul-template && git checkout ${GH_TAGNAME}
# ${LOCALBASE}/bin/dep init
# rm -rf .git/
# cd .. && mv consul-template consul-template-${GH_TAGNAME#v*}
# tar czf consul-template-${GH_TAGNAME#v*}.tar.gz consul-template-${GH_TAGNAME#v*}

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/consul-template
	${INSTALL_DATA} ${WRKSRC}/examples/* ${FILESDIR}/default.conf \
		${PREFIX}/share/examples/consul-template

.include <bsd.port.mk>
