<p align="center">
		<img src=".github/header.png" width="1200" alt="Docker Images Logo">
</p>
<p align="center">
	<a href="https://actions-badge.atrox.dev/serversideup/docker-ssh/goto?ref=main"><img alt="Build Status" src="https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2Fserversideup%2Fdocker-ssh%2Fbadge%3Fref%3Dmain&style=flat" /></a>
	<a href="https://github.com/serversideup/docker-ssh/blob/main/LICENSE" target="_blank"><img src="https://badgen.net/github/license/serversideup/docker-ssh" alt="License"></a>
	<a href="https://github.com/sponsors/serversideup"><img src="https://badgen.net/badge/icon/Support%20Us?label=GitHub%20Sponsors&color=orange" alt="Support us"></a>
</p>

# About this project
This is a super simple SSHD container based on Ubuntu 20.04.

# What this image does
It does one thing very well:

* It's a hardened SSH server (perfect for encrypted tunnels into your cluser)
* Set authorized keys via the `AUTHORIZED_KEYS` environment variable
* Set authorized IP addresses via the `ALLOWED_IPS` environment variable
* It also includes the `ping` tool for troubleshooting connections
* It's automatically updated nightly via Github actions

# Usage instructions

### 1. Set your `AUTHORIZED_KEYS` environment variable
```
AUTHORIZED_KEYS="$(cat .ssh/my_many_ssh_public_keys_in_one_file.txt)"
```
### 2. Set your `ALLOWED_IPS` environment variable
This example shows a few scenarios you can do:
```
ALLOWED_IPS="AllowUsers *@192.168.1.0/24 *@172.16.0.1 *@10.0.*.1"
```

### 3. Forward your external port to `2222` on the container
You can see that I am forwarding `12345` to `2222`.
```
docker run --rm --name=ssh --network=web -p 12345:2222 localhost/ssh
```
This means I would connect with:
```
ssh -p 12345 tunnel@myserver.test
```

# Questions
Open up an issue and we'll get back to you!