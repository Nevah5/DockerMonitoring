FROM postgres:9.6.2-alpine

RUN apk update                                                                                    \
  apk add dpkg                                                                                    \
  wget https://github.com/Nevah5/DockerMonitoring/blob/master/check-mk-agent_2.0.0p16-1_all.deb   \
  dpkg -i check-mk-agent_2.0.0p16-1_all.deb