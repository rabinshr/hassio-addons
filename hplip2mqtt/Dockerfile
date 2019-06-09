# Docker file to create an image for a hass.io add-on that contains enough software to query a HP network printer via <hplip> and publish the ink levels to a MQTT broker.

ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

MAINTAINER James Fry & Bouwe Westerdijk

LABEL Description="This image is used to start a script that will monitor for RF events on 433Mhz (configurable) and send the data to an MQTT server"

#
# First install software packages needed to compile rtl_433 and to publish MQTT events
#

RUN \
apk add --no-cache --virtual build-deps alpine-sdk cmake libusb-dev python3-dev cups cups-dev jpeg-dev && \
mkdir /tmp/src && \
cd /tmp/src && \
curl -L https://downloads.sourceforge.net/project/hplip/hplip/3.19.5/hplip-3.19.5.tar.gz -o hplip.tar.gz && \
tar xvfz hplip.tar.gz && \
cd hplip-3.19.5 && \
./configure --disable-network-build
#&& \
#make && \
#make install && \
#apk add --no-cache mosquitto-clients jq
#
#
# Define an environment variable
#
# Use this variable when creating a container to specify the MQTT broker host.
ENV MQTT_HOST="hassio.local"
ENV MQTT_USER="guest"
ENV MQTT_PASS="guest"
ENV MQTT_TOPIC="homeassistant/sensor/ink"

CMD cd / && cp /config/hplip2mqtt/hplip2mqtt.sh /hplip2mqtt.sh && chmod +x /hplip2mqtt.sh && /hplip2mqtt.sh

