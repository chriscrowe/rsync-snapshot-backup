# ARG BUILD_FROM
FROM ubuntu:focal

# Add env
ENV LANG C.UTF-8

# Setup base
RUN apt update
RUN apt install -y jq sshpass rsync

# Hass.io CLI
ARG BUILD_ARCH
ARG CLI_VERSION
RUN apt install -y curl \
    && curl -Lso /usr/bin/ha https://github.com/home-assistant/cli/releases/latest/download/ha_${BUILD_ARCH} \
    && chmod a+x /usr/bin/ha

# Copy data
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]

# Build arugments
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="rsync Snapshot Backup" \
    io.hass.description="Automatically create HomeAssistant snapshots backup to remote server using `rsync`." \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Sarabveer Singh <me@sarabveer.me>" \
    org.label-schema.description="Automatically create HomeAssistant snapshots and backup to remote server using `rsync`." \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="rsync Snapshot Backup" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.usage="https://github.com/sarabveer/rsync-snapshot-backup/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/sarabveer/rsync-snapshot-backup/" \
    org.label-schema.vendor="HomeAssistant add-ons by Sarabveer Singh"
