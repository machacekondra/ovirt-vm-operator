FROM quay.io/operator-framework/ansible-operator:v0.8.0

USER root
RUN yum install -y nss-devel gcc libcurl-devel libxml2-devel python-devel && PYCURL_SSL_LIBRARY=nss pip install -U ansible ovirt-engine-sdk-python
USER 1001

COPY watches.yaml ${HOME}/watches.yaml

COPY roles/ ${HOME}/roles/

ENTRYPOINT ["/usr/local/bin/entrypoint", "--inject-owner-ref=false"]
