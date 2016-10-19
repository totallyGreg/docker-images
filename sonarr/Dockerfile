FROM linuxserver/sonarr:latest
LABEL org.freenas.interactive="false" \
      org.freenas.upgradeable="true" \
      org.freenas.expose-ports-at-host="true" \
      org.freenas.autostart="true" \
      org.freenas.web-ui-protocol="http" \
      org.freenas.web-ui-port=8989 \
      org.freenas.web-ui-path="" \
      org.freenas.port-mappings="8989:8989/tcp" \
      org.freenas.volumes="[						\
          {								\
              \"name\": \"/config\",					\
              \"descr\": \"Database and Sonarr configs\"		\
          },								\
          {								\
              \"name\": \"/dev/rtc\",					\
              \"readonly\": \"true\"					\
              \"descr\": \"hwclock r/o mapping\"			\
          },								\
          {								\
              \"name\": \"/tv\",					\
              \"descr\": \"Location of TV library\"			\
          }								\
      ]" 
