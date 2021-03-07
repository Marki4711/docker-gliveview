#FROM inputoutput/cardano-node
FROM registry.gitlab.com/viper-staking/docker-containers/cardano-node:latest

USER root

RUN apt update -y &&\
  apt install curl apt-utils procps -y 

# prereqs for cnode-helper-scripts
ENV SUDO="N"
ADD https://raw.githubusercontent.com/cardano-community/guild-operators/master/scripts/cnode-helper-scripts/prereqs.sh /prereqs.sh
RUN chmod 755 prereqs.sh
RUN ./prereqs.sh

# gLiveView
ADD https://raw.githubusercontent.com/cardano-community/guild-operators/master/scripts/cnode-helper-scripts/gLiveView.sh /gliveview/
ADD https://raw.githubusercontent.com/cardano-community/guild-operators/master/scripts/cnode-helper-scripts/env /gliveview/
RUN sed -i '/CNODE_PORT=6000/d' /gliveview/env
RUN chmod 755 /gliveview/prereqs.sh

ENTRYPOINT echo "Container is running and sleeping" ; sleep infinity
