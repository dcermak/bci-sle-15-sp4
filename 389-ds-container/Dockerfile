# SPDX-License-Identifier: MIT
#!BuildTag: suse/389-ds:%%389ds_version%%
#!BuildTag: suse/389-ds:latest
#!BuildTag: suse/389-ds:%%389ds_version%%-%RELEASE%
#!BuildVersion: 15.4
FROM suse/sle15:15.4

MAINTAINER wbrown@suse.de

# Define labels according to https://en.opensuse.org/Building_derived_containers
# labelprefix=com.suse.application.389-ds
LABEL org.opencontainers.image.title="SLE 389 Directory Server Container Image"
LABEL org.opencontainers.image.description="389 Directory Server based on the SLE Base Container Image."
LABEL org.opencontainers.image.version="%%389ds_version%%"
LABEL org.opencontainers.image.url="https://www.suse.com/products/server/"
LABEL org.opencontainers.image.created="%BUILDTIME%"
LABEL org.opencontainers.image.vendor="SUSE LLC"
LABEL org.opensuse.reference="registry.suse.com/suse/389-ds:%%389ds_version%%-%RELEASE%"
LABEL org.openbuildservice.disturl="%DISTURL%"
LABEL com.suse.supportlevel="techpreview"
LABEL com.suse.eula="sle-bci"
LABEL com.suse.lifecycle-url="https://www.suse.com/lifecycle"
LABEL com.suse.image-type="application"
LABEL com.suse.release-stage="released"
# endlabelprefix


RUN set -euo pipefail; zypper -n in --no-recommends 389-ds timezone openssl; zypper -n clean; rm -rf /var/log/*



CMD ["/usr/lib/dirsrv/dscontainer", "-r"]
EXPOSE 3389 3636

RUN set -euo pipefail; mkdir -p /data/config; \
    mkdir -p /data/ssca; \
    mkdir -p /data/run; \
    mkdir -p /var/run/dirsrv; \
    ln -s /data/config /etc/dirsrv/slapd-localhost; \
    ln -s /data/ssca /etc/dirsrv/ssca; \
    ln -s /data/run /var/run/dirsrv

VOLUME /data

HEALTHCHECK --start-period=5m --timeout=5s --interval=5s --retries=2 \
    CMD /usr/lib/dirsrv/dscontainer -H
