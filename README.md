# Ansible role: argosd
[![Build Status](https://travis-ci.org/danielkoster/ansible-role-argosd.svg?branch=master)](https://travis-ci.org/danielkoster/ansible-role-argosd)
[![Ansible Role](https://img.shields.io/ansible/role/16212.svg)](https://galaxy.ansible.com/danielkoster/argosd/)

Installs and configures [ArgosD](https://github.com/danielkoster/argosd) on Debian/Ubuntu servers.

## Requirements
There are no special requirements. Note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

```yaml
- hosts: argosd
  roles:
    - role: danielkoster.argosd
      become: yes
```

## Role Variables
Available variables are listed below, along with default values (see `defaults/main.yml`).

```yaml
argosd_rss_feed: ''
```
The URL to your RSS-feed. This should be a feed containing a channel with items that have a title and a link. 

```yaml
argosd_transmission_host: 'localhost'
argosd_transmission_port: 9091
argosd_transmission_username: ''
argosd_transmission_password: ''
```
Specify how we can connect to the Transmission server. An RPC connection is made, so check these settings in Transmission.

```yaml
argosd_api_token: ''
```
Create an API token. You will have to send this token with each API request you make. Keep it safe!

```yaml
argosd_torrentclient_download_dir: ''
```
Override for the download directory where the torrentclient will download the episodes to. If undefined, episodes will be downloaded to the default location as determined by the torrentclient.

```yaml
argosd_telegram_bot_token: ''
```
Optional token for Telegram bot. This bot will send you notifications whenever a new episode is downloaded.

## Example Playbook
```yaml
- hosts: argosd
  become: yes
  roles:
    - { role: danielkoster.argosd }
```

*Inside `vars/main.yml`*:
```yaml
argosd_transmission_host: '192.168.178.4'
argosd_transmission_port: 1337
```
