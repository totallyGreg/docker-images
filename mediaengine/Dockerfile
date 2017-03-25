FROM linuxserver/deluge:latest
LABEL org.freenas.interactive="false"                                                           \
      org.freenas.version="1.3.14"                                                              \
      org.freenas.upgradeable="true"                                                            \
      org.freenas.expose-ports-at-host="true"                                                   \
      org.freenas.autostart="true"                                                              \
      org.freenas.web-ui-protocol="http"                                                        \
      org.freenas.web-ui-port=8112                                                              \
      org.freenas.web-ui-path=""                                                                \
      org.freenas.port-mappings="8112:8112/tcp,58846:58846/tcp,58946:58946/tcp,58946:58946/udp" \
      org.freenas.volumes="[                                                                    \
          {                                                                                     \
              \"name\": \"/config\",                                                            \
              \"descr\": \"Config storage space\"                                               \
          },                                                                                    \
          {                                                                                     \
              \"name\": \"/scripts\",                                                            \
              \"descr\": \"Scripts storage space\"                                               \
          },                                                                                    \
          {                                                                                     \
              \"name\": \"/downloads\",                                                         \
              \"descr\": \"Downloads volume\"                                                   \
          }                                                                                     \
      ]"                                                                                        \
      org.freenas.settings="[                                                                   \
          {                                                                                     \
              \"env\": \"TZ\",                                                                  \
              \"descr\": \"Timezone - eg Europe/London\",                                       \
              \"optional\": true                                                                \
          },                                                                                    \
          {                                                                                     \
              \"env\": \"PGID\",                                                                \
              \"descr\": \"GroupID\",                                                           \
              \"optional\": true                                                                \
          },                                                                                    \
          {                                                                                     \
              \"env\": \"PUID\",                                                                \
              \"descr\": \"UserID\",                                                            \
              \"optional\": true                                                                \
         }                                                                                      \
      ]"


# OS update & package installation
RUN apk -U upgrade && \
    apk -U add \
        py2-pip \
        ca-certificates \
        git \
        python \
        py-libxml2 \
        py-lxml \
        make \
        gcc \
        g++ \
        python-dev \
        openssl \
        openssl-dev \
        libffi-dev \
        unrar \
        tzdata

# pip package installation
RUN pip install --upgrade pip && \
    pip --no-cache-dir install --upgrade setuptools && \
    pip --no-cache-dir install --upgrade pyopenssl \
        requests \
        requests[security] \
        requests-cache \
        cheetah \
        babelfish \
        "guessit<2" \
        "subliminal<2" \
        stevedore==1.19.1 \
        python-dateutil \
        deluge-client \
        qtfaststart \
        requirements

RUN cp /usr/share/zoneinfo/US/Eastern /etc/localtime

WORKDIR /tmp

# clone ffmpeg
RUN wget -q https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-64bit-static.tar.xz && \
    tar xJf ffmpeg-release-64bit-static.tar.xz && \
    mv ffmpeg-*-64bit-static/ffmpeg /usr/local/bin/ && \
    mv ffmpeg-*-64bit-static/ffprobe /usr/local/bin/ && \
    rm -rf ffmpeg*



