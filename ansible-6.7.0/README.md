# Introduction

This Dockerfile builds a Debian 11.6 (Bullseye) image with Ansible, AWS CLI and `pcluster` installed.

## Software versions

- ansible [core 2.13.11]
- Python 3.9.2
- aws-cli/1.29.40
- pcluster 3.7.0

## Building the image

Set the variables.

```bash
ANSIBLE_VER='6.7.0'
REGISTRY="cloudguyinbroadstone"
REPO="ansible-${ANSIBLE_VER}"
TAG='1.1'
```

Build the image.

```bash
docker build --pull --no-cache -t ${REPO}:${TAG} -f ${REPO}/Dockerfile ${REPO}
```

Login to Docker hub.

```sh
cat ~/my_password.txt | docker login --username cloudguyinbroadstone --password-stdin
```

Tag and push

```sh
docker tag ${REPO}:${TAG} ${REGISTRY}/${REPO}:${TAG}
docker tag ${REPO}:${TAG} ${REGISTRY}/${REPO}:latest
```

```sh
docker push ${REGISTRY}/${REPO}:${TAG}
```
