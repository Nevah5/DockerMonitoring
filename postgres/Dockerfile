FROM postgres:9.6.2-alpine

RUN apk update && apk upgrade -y                \
  apk add dpkg                                  \
  dpkg -i check-mk-agent_2.0.0p42-1_all.deb