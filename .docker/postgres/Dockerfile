FROM postgres:9.6.2-alpine AS postgres

RUN apk update
RUN apk add dpkg
RUN apk add wget
RUN apk add sudo
# RUN sudo wget https://github.com/Nevah5/DockerMonitoring/blob/master/check-mk-agent_2.0.0p16-1_all.deb --no-check-certificate
# RUN sudo dpkg -i check-mk-agent_2.0.0p16-1_all.deb
# RUN rpm -U http://mycmkserver/mysite/check_mk/agents/check-mk-agent-2.0.0p42-1.noarch.rpm