FROM ictf_base

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y nginx uwsgi uwsgi-plugin-python3 mysql-server python3-pip virtualenv python-mysqldb python3-dev 
RUN pip3 install --upgrade pip pyOpenSSL ndg-httpsclient pyasn1

COPY ./database /opt/ictf/database
COPY ./scoring_ictf /opt/ictf/scoring_ictf

WORKDIR /opt/ictf/database

RUN chmod +x ./start.sh && ansible-playbook ./provisioning/hephaestus_provisioning/ansible-provisioning.yml

ENTRYPOINT ./start.sh