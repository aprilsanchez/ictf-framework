FROM ictf_base

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends iptraf python3-pip python3-dev build-essential awscli iptables-persistent iftop libcurl4-openssl-dev libssl-dev python3-apt zip unzip openvpn

COPY ./router /opt/ictf/router

WORKDIR /opt/ictf/router

# RUN apt install python3-vagrant

RUN pip3 install -r requirements2.txt

RUN ansible-playbook provisioning/hephaestus_provisioning/ansible-provisioning.yml --become 

RUN chmod +x ./start.sh

ENTRYPOINT ./start.sh