FROM docker.io/certbot/certbot:v3.1.0

RUN pip install --upgrade pip
COPY certbot-dns-oci/requirements.txt /usr/local/src/certbot-dns-oci/requirements.txt
RUN pip install --requirement /usr/local/src/certbot-dns-oci/requirements.txt
COPY certbot-dns-oci/build-requirements.txt /usr/local/src/certbot-dns-oci/build-requirements.txt
RUN pip install --requirement /usr/local/src/certbot-dns-oci/build-requirements.txt
COPY certbot-dns-oci /usr/local/src/certbot-dns-oci
ENV PBR_VERSION=0.9.0
RUN pip install --use-pep517 --editable /usr/local/src/certbot-dns-oci

ENTRYPOINT [ "certbot", "certonly", "--non-interactive", "--agree-tos", "--preferred-challenge", "dns-01", "--authenticator", "dns-oci" ]

VOLUME [ "/etc/letsencrypt" ]  # Config
VOLUME [ "/var/lib/letsencrypt" ]  # Work
VOLUME [ "/var/log/letsencrypt" ]  # Logs
