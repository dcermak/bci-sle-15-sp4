# SPDX-License-Identifier: MIT
#!BuildTag: bci/golang:1.16
#!BuildTag: bci/golang:1.16-%RELEASE%
#!BuildVersion: 15.4
FROM suse/sle15:15.4

MAINTAINER SUSE LLC (https://www.suse.com/)

# Define labels according to https://en.opensuse.org/Building_derived_containers
# labelprefix=com.suse.bci.golang
LABEL org.opencontainers.image.title="SLE BCI Golang 1.16 Container Image"
LABEL org.opencontainers.image.description="Golang 1.16 development environment based on the SLE Base Container Image."
LABEL org.opencontainers.image.version="1.16"
LABEL org.opencontainers.image.url="https://www.suse.com/products/server/"
LABEL org.opencontainers.image.created="%BUILDTIME%"
LABEL org.opencontainers.image.vendor="SUSE LLC"
LABEL org.opensuse.reference="registry.suse.com/bci/golang:1.16-%RELEASE%"
LABEL org.openbuildservice.disturl="%DISTURL%"
LABEL com.suse.supportlevel="techpreview"
LABEL com.suse.eula="sle-bci"
LABEL com.suse.lifecycle-url="https://www.suse.com/lifecycle"
LABEL com.suse.image-type="sle-bci"
LABEL com.suse.release-stage="released"
# endlabelprefix


RUN set -euo pipefail; zypper -n in --no-recommends go1.16 distribution-release make git-core; zypper -n clean; rm -rf /var/log/*

ENV GOLANG_VERSION="%%golang_version%%"
ENV GOPATH="/go"
ENV PATH="/go/bin:/usr/local/go/bin:/root/go/bin/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"


