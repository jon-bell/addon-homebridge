ARG BUILD_FROM=homebridge/homebridge:latest
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV CONFIG_PATH=/data/options.json
ENV ENABLE_AVAHI=0

# Copy root filesystem
# COPY rootfs /
RUN ln -s /data /homebridge

# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Homebridge" \
    io.hass.description="HomeKit support for your Home Assistant instance using Homebridge" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Jonathan Bell <jon@jonbell.net>" \
    org.label-schema.description="HomeKit support for your Home Assistant instance using Homebridge" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Homebridge" \
    org.label-schema.schema-version="2.0" \
    org.label-schema.usage="https://github.com/jon-bell/addon-homebridge/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/jon-bell/addon-homebridge" \
    org.label-schema.vendor="Community Hass.io Add-ons"

EXPOSE 8581/tcp
WORKDIR /homebridge

ENTRYPOINT [ "/init" ]