# SPDX-License-Identifier: MIT
#!BuildTag: bci/openjdk-devel:11
#!BuildTag: bci/openjdk-devel:latest
#!BuildTag: bci/openjdk-devel:11-%RELEASE%
#!BuildVersion: 15.4
FROM bci/openjdk:11

MAINTAINER SUSE LLC (https://www.suse.com/)

# Define labels according to https://en.opensuse.org/Building_derived_containers
# labelprefix=com.suse.bci.openjdk.devel
LABEL org.opencontainers.image.title="SLE BCI OpenJDK 11 Development Container Image"
LABEL org.opencontainers.image.description="Java 11 Development environment based on the SLE Base Container Image."
LABEL org.opencontainers.image.version="11"
LABEL org.opencontainers.image.url="https://www.suse.com/products/server/"
LABEL org.opencontainers.image.created="%BUILDTIME%"
LABEL org.opencontainers.image.vendor="SUSE LLC"
LABEL org.opensuse.reference="registry.suse.com/bci/openjdk-devel:11-%RELEASE%"
LABEL org.openbuildservice.disturl="%DISTURL%"
LABEL com.suse.supportlevel="techpreview"
LABEL com.suse.eula="sle-bci"
LABEL com.suse.lifecycle-url="https://www.suse.com/lifecycle"
LABEL com.suse.image-type="sle-bci"
LABEL com.suse.release-stage="released"
# endlabelprefix


RUN set -euo pipefail; zypper -n in --no-recommends java-11-openjdk-devel git-core maven; zypper -n clean; rm -rf /var/log/*

ENV JAVA_BINDIR="/usr/lib64/jvm/java/bin"
ENV JAVA_HOME="/usr/lib64/jvm/java"
ENV JAVA_ROOT="/usr/lib64/jvm/java"
ENV JAVA_VERSION="11"

CMD ["/usr/bin/jshell"]
