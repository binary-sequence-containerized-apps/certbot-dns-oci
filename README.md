# certbot-dns-oci

This project is supposed to be temporary until https://github.com/ITD27M01/certbot-dns-oci/pull/10 is fixed

## Build image

```sh
podman build -t certbot-dns-oci ./build-context/
```

## Run container

### Dry run

```sh
podman run --rm --name certbot-dns-oci -v ~/.oci:/root/.oci:ro certbot-dns-oci --dns-oci-profile <yourprofile> --email <youremail> --domain your.domain.com --dry-run
```

### Request certificate

```sh
mkdir ./letsencrypt
podman run --rm --name certbot-dns-oci -v ~/.oci:/root/.oci:ro -v ./letsencrypt:/etc/letsencrypt certbot-dns-oci --dns-oci-profile <yourprofile> --email <youremail> --domain your.domain.com
```
