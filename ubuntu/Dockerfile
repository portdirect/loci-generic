ARG FROM=ubuntu:xenial
FROM ${FROM}

ENV PATH=/var/lib/openstack/bin:$PATH
ARG PROJECT
ARG WHEELS=openstackloci/requirements:ubuntu
ARG PROJECT_REPO=https://git.openstack.org/openstack/${PROJECT}
ARG PROJECT_REF=master
ARG SCRIPTS_REPO=https://github.com/openstack/loci
ARG SCRIPTS_REF=master
ARG DISTRO
ARG DIST_PACKAGES
ARG PYPI_PACKAGES

RUN set -x \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends $DIST_PACKAGES \
        git \
        ca-certificates \
    && git init /tmp/common/ \
    && git --git-dir /tmp/common/.git fetch --depth 1 $SCRIPTS_REPO $SCRIPTS_REF \
    && git --work-tree /tmp/common --git-dir /tmp/common/.git checkout FETCH_HEAD \
    && /tmp/common/scripts/install.sh $PYPI_PACKAGES
