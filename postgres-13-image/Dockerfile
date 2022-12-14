# SPDX-License-Identifier: MIT
#!BuildTag: suse/postgres:13
#!BuildTag: suse/postgres:13-%RELEASE%
#!BuildTag: suse/postgres:%%pg_version%%
#!BuildVersion: 15.4
FROM suse/sle15:15.4

MAINTAINER SUSE LLC (https://www.suse.com/)

# Define labels according to https://en.opensuse.org/Building_derived_containers
# labelprefix=com.suse.application.postgres
LABEL org.opencontainers.image.title="SLE PostgreSQL 13 Container Image"
LABEL org.opencontainers.image.description="PostgreSQL 13 based on the SLE Base Container Image."
LABEL org.opencontainers.image.version="13"
LABEL org.opencontainers.image.url="https://www.suse.com/products/server/"
LABEL org.opencontainers.image.created="%BUILDTIME%"
LABEL org.opencontainers.image.vendor="SUSE LLC"
LABEL org.opensuse.reference="registry.suse.com/suse/postgres:13-%RELEASE%"
LABEL org.openbuildservice.disturl="%DISTURL%"
LABEL com.suse.supportlevel="techpreview"
LABEL com.suse.eula="sle-bci"
LABEL com.suse.lifecycle-url="https://www.suse.com/lifecycle"
LABEL com.suse.image-type="application"
LABEL com.suse.release-stage="released"
# endlabelprefix


RUN set -euo pipefail; zypper -n in --no-recommends postgresql13-server distribution-release; zypper -n clean; rm -rf /var/log/*

ENV LANG="en_US.utf8"
ENV PG_MAJOR="13"
ENV PG_VERSION="%%pg_version%%"
ENV PGDATA="/var/lib/postgresql/data"
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["postgres"]

VOLUME /var/lib/postgresql/data

COPY docker-entrypoint.sh /usr/local/bin/
RUN set -euo pipefail; chmod +x /usr/local/bin/docker-entrypoint.sh; \
    ln -s su /usr/bin/gosu; \
    mkdir /docker-entrypoint-initdb.d; \
    sed -ri "s|^#?(listen_addresses)\s*=\s*\S+.*|\1 = '*'|" /usr/share/postgresql13/postgresql.conf.sample

STOPSIGNAL SIGINT
EXPOSE 5432
