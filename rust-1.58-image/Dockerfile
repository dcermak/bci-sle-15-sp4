# SPDX-License-Identifier: MIT
#!BuildTag: bci/rust:1.58
#!BuildTag: bci/rust:1.58-%RELEASE%
FROM suse/sle15:15.4

MAINTAINER SUSE LLC (https://www.suse.com/)

# Define labels according to https://en.opensuse.org/Building_derived_containers
# labelprefix=com.suse.bci.rust
LABEL org.opencontainers.image.title="SLE BCI Rust 1.58 Container Image"
LABEL org.opencontainers.image.description="Rust 1.58 based on the SLE Base Container Image."
LABEL org.opencontainers.image.version="1.58"
LABEL org.opencontainers.image.url="https://www.suse.com/products/server/"
LABEL org.opencontainers.image.created="%BUILDTIME%"
LABEL org.opencontainers.image.vendor="SUSE LLC"
LABEL org.opensuse.reference="registry.suse.com/bci/rust:1.58-%RELEASE%"
LABEL org.openbuildservice.disturl="%DISTURL%"
LABEL com.suse.supportlevel="techpreview"
LABEL com.suse.eula="sle-bci"
LABEL com.suse.lifecycle-url="https://www.suse.com/lifecycle"
LABEL com.suse.image-type="sle-bci"
LABEL com.suse.release-stage="released"
# endlabelprefix


RUN set -euo pipefail; zypper -n in --no-recommends rust1.58 cargo1.58 distribution-release; zypper -n clean; rm -rf /var/log/*

ENV RUST_VERSION="%%RUST_VERSION%%"
ENV CARGO_VERSION="%%CARGO_VERSION%%"


