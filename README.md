# RaspberryPi Network Sharing Passive Income Setup with Docker

Docker stack that runs these passive-income apps in one single docker-compose file which are rasberrypi supported.

With this project, you can start earning money doing nothing through a curated list of passive income applications.
You can use this project on any device that supports docker. This includes : Raspberry Pi, Synology NAS, a VPS, Windows, MacOS, Linux... 

# Table of content

- [Requirements](#1-requirements)
  + [Docker](#docker)
  + [Docker-Compose](#docker-compose)
- [Installation](#2-installation)
- [Configuration](#3-configuration)
	+ [Peer2Profit](#-peer2profit)
	+ [PacketStream](#-packetstream)
	+ [HoneyGain](#-honeygain)
	+ [EarnApp](#-earnapp)
	+ [Repocket](#-repocket)
	+ [TraffMonetizer](#-traffmonetizer)
	+ [Pawns](#-pawns)
	+ [Bitping](#-bitping)
	+ [ProxyRack](#-proxyrack) <span style="color:gray">Not runs well with raspberrypi.</span>
  + [ProxyLite](#-proxylite) <span style="color:gray">Not runs well with raspberrypi</span>
- [Running the stack](#4-running-the-stack)
- [Support](#5-support)

-------------
# 1. Requirements

This project uses Docker and Docker-Compose **only**


## Docker

Follow the steps to install Docker if you don't have it already.

The steps can be found here: https://docs.docker.com/get-docker/

For your convenience, here are the steps to install Docker on a Debian/Raspbian OS :

```
sudo apt-get update && sudo apt-get upgrade
curl -fsSL test.docker.com -o get-docker.sh && sh get-docker.sh
sudo usermod -aG docker docker_user
sudo usermod -aG docker ${USER}
groups ${USER}
sudo systemctl enable docker
sudo reboot
```

## Docker-Compose

Follow the steps to install Docker-Compose if you don't have it already.

The steps can be found here: https://docs.docker.com/compose/install/
For your convenience, here are the steps to install Docker-Compose on a Debian/Raspbian OS :

```
sudo apt-get install libffi-dev libssl-dev
sudo apt install python3-dev
sudo apt-get install -y python3 python3-pip
sudo pip3 install docker-compose

- OR -

sudo apt install docker-compose
```

-------------
# 2. Installation

First, clone this repository.

Here are two different techniques

- Method 1: Download as Zip

On this webpage, click on the green button "<> Code" and then "Download ZIP".
Unzip the zip, and verify that you have a folder named `p-income` containing this repo.

- Method 2: Using git clone

The following command will create a folder `` and clone the repository inside it.

```
git clone https://github.com/amitk030/p-income.git p-income
cd p-income
```

Once done, I recommend that you move the directory called `p-income` to somewhere safe on your device. Don't leave it in the `Downloads` folder, because you might delete it in the future.


-------------
# 3. Configuration

The following steps will guide you through the account creation and the configuration.

During these steps, you'll be required to open your copy of the [`.env`](.env) located in your `p-income` directory with a text editor such as `vim`, `sublime text`, `NotePad`, `TextEdit`. Then, follow the next steps and find/replace each "Variable" by your own value (email address, password, identification, ... it depends on the application).

## Yields

These apps won't use much RAM/CPU, but should you need to narrow down these apps to the best ones only, each app is ranked using the following emojis:

- 🟩 High yield earnings
- 🟧 Medium yield earnings
- 🟫 Low yield earnings
- 🟥 Very low yield earnings
 
Feel free to remove the apps you do not want by simply commenting the relevant configuration part in the [`docker-compose.yaml`](docker-compose.yaml).

Please note that this rank is based on my experience using those apps in IND (the earnings depends mostly on your location but also internet speed and other factors).
If you do not live in the IND, I recommend that you try them out first and review the earnings after a few weeks.

## 🟩 Peer2Profit

### Account creation

Create your account on the following telegram channel. Peer2Profit no longer have a website, everything is performed through a Telegram channel (Payouts, Balance, ...)

[https://t.me/peer2profit_app_bot](https://t.me/peer2profit_app_bot "https://t.me/peer2profit_app_bot")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PEER2PROFIT_EMAIL_ADDRESS`  | Peer2Profit account address |


## 🟩 PacketStream

### Account creation

Create your account on the following website

[https://packetstream.io](https://packetstream.io/?psr=6Mc2 "https://packetstream.io")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PACKETSTREAM_CID`  | PacketStream referral ID (4 characters), which can be found in your referral link, the last 4 characters https://packetstream.io/dashboard/referrals |

Note that if you changed the name of the folder in which the [`.env`](.env) is located (by default `p-income`, see section [1. Installation](#installation)), then edit the following:

| Variable  | Description |
| --------- | -----|
| `p-income_psclient_1` | Change this variable to `NAME_OF_FOLDER` followed by `_psclient_1` (remove any spaces that might be in the name of your folder) |


## 🟩 HoneyGain

### Account creation

Create your account on the following website

[https://r.honeygain.me](https://r.honeygain.me/AM03AF87BA "https://r.honeygain.me")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_HONEYGAIN_EMAIL_ADDRESS`  | HoneyGain account address |
| `YOUR_USER_HONEYGAIN_PASSWORD`  |   HoneyGain account password |
| `-device`  | (optional) A device name for display purposes, default is `EarningMachine` must be unique per IP/machine |


## 🟧 EarnApp

### Account creation

Create your account on the following website

[https://earnapp.com](https://earnapp.com/i/FmVufBDz "https://earnapp.com")

### Generate your Node id

Execute the following command :

```
docker run --privileged --rm -v /sys/fs/cgroup:/sys/fs/cgroup:ro --name earnapp fazalfarhan01/earnapp:lite /bin/bash -c "apt-get update && apt install -y systemctl && /download/earnapp install && cat /etc/earnapp/uuid"
```

This command will generate and output a node id with the following pattern : 
`sdk-node-xxxxxxxxxxxxxxxxxxxx`.

### Link your node id

Link your newly created node id to your account by following the steps here:

(Replace `YOUR_NODE_ID` with your node id)

https://earnapp.com/r/YOUR_NODE_ID

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_EARNAPP_NODE_ID`  | EarnApp Node Id |


## 🟫 ProxyLite

### Account creation

Create your account on the following website

[https://proxylite.ru](https://proxylite.ru/?r=Q0PF8FKQ "https://proxylite.ru/")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PROXYLITE_ACCOUNT_ID`  | ProxyLite Account id can be found in the dashboard (https://lk.proxylite.ru/index.php/) |

## 🟫 Repocket

### Account creation

Create your account on the following website

[https://link.repocket.co](https://link.repocket.com/cUzV "https://link.repocket.co")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_REPOCKET_EMAIL_ADDRESS`  | Repocket account address |
| `YOUR_REPOCKET_API_KEY`  | Repocket API Key can be found in the dashboard (https://app.repocket.co/) |


## 🟫 TraffMonetizer

### Account creation

Create your account on the following website

[https://traffmonetizer.com](https://traffmonetizer.com/?aff=1701236 "https://traffmonetizer.com")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_TRAFFMONETIZER_TOKEN`  | TraffMonetizer token that can be found in the dashboard (https://app.traffmonetizer.com/dashboard) on the top left corner "Your application token" |


## 🟫 Pawns

### Account creation

Create your account on the following website

[https://pawns.app](https://pawns.app/?r=4499175 "https://pawns.app")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PAWNS_EMAIL_ADDRESS`  | Pawns account address |
| `YOUR_PAWNS_USER_PASSWORD`  | Pawns account password |


## 🟥 Bitping

### Account creation

Create your account on the following website

[https://app.bitping.com](https://app.bitping.com "https://app.bitping.com")

### Generate configuration file

Execute the following command and follow the BitPing steps (enter your BitPing credentials) to generate a configuration file

`sudo docker run -it -v $(pwd)/data/bitping/:/root/.bitping bitping/bitping-node:latest`

When `Successfully logged in to Bitping` is displayed, you can safely kill the container with `CTRL+C` or `CMD+C`.


## 🟥 ProxyRack

### Account creation

Create your account on the following website

[https://peer.proxyrack.com/register](https://peer.proxyrack.com/ref/ppmtzeo4kd35c8idcs1jxcownsdejzzsjywpagpy "https://peer.proxyrack.com/register")

### update `.env`

In the [`.env`](.env), edit :

| Variable  | Description |
| --------- | -----|
| `YOUR_PROXYRACK_API_KEY`  | ProxyRack Api key can be generated in the profile section of your account (https://peer.proxyrack.com/profile) |
| `device_name`  | (optional) A device name for display purposes, default is `EarningMachine` must be unique per IP/machine |


-------------
# 4. Running the stack

To run the stack and start earning money, execute the following command in this project directory (the folder `p-income`):

`docker-compose up -d`

To check the running containers check:
`docker ps`

-------------
# 5. Support

If you have any questions, feel free to open an issue here, I'll answer.

If you like this project, use the referral links provided on this README.md file to support it.

Alternatively, consider donating.

<a href="https://www.buymeacoffee.com/amkumar030k" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-yellow.png" alt="Buy Me A Coffee" height="50" width="200"></a>