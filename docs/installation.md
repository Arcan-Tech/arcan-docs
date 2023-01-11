---
title: Install Arcan 


---

# Install Arcan

## Requirements for native Docker execution mode
- Docker Engine >= 20.10 (See [https://docs.docker.com/engine/install](https://docs.docker.com/engine/install))
- Docker Compose (See [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/))

## Requirements for VM-based Docker execution mode using [Vagrant](https://developer.hashicorp.com/vagrant)
- Vagrant
- VirtualBox

## How to run Arcan locally
First, [Clone](https://github.com/Arcan-Tech/arcan-trial) or [download](https://github.com/Arcan-Tech/arcan-trial/archive/refs/heads/main.zip) Arcan from Github. Then, follow the instructions below.

### Obtain the licence file
- Fill in this [form](https://www.arcan.tech/on-premise-trial/). You will receive the license at the provided email address.
- Open the email and download the attached `ArcanLicence_YYYYMMDD` licence file.
- Copy the `ArcanLicence_YYYYMMDD` licence file to the [licences](https://github.com/Arcan-Tech/arcan-trial/tree/main/licences) directory.

### Configure the environment
- Copy the content of the [.env.example](https://github.com/Arcan-Tech/arcan-trial/blob/main/.env.example) file into a new file named `.env`.
- Change the value of the variable `ARCAN_LICENCE_FILENAME` with the name of licence file you copied in the [licences](https://github.com/Arcan-Tech/arcan-trial/tree/main/licences) directory.

### Run Arcan with native Docker execution mode
- To run the Arcan dashboard and the server, open your favourite terminal and navigate to the `/arcan-trial` folder. Within the folder execute: `docker compose up`.
- You will find the dashboard at [http://localhost:3000](http://localhost:3000).
- To analyse a *remote* project, simply use the remote repo url when creating a new project. If the repo is private, remember to use a personal access token as password (see the [documentation](./documentation) for more info).
- To analyse a *local* project, copy the project folder into `/arcan-trial/projects`. When creating a new project, specify the path to analyse as follows: `./projects/<folder_name>`  (see the [documentation](./documentation) for more info).

### Run Arcan with VM-based Docker execution mode using [Vagrant](https://developer.hashicorp.com/vagrant)
- To run the Arcan dashboard and the server, open your favourite terminal and navigate to the `/arcan-trial` folder. Within the folder execute: `vagrant up`.
- You will find the dashboard at [http://localhost:3000](http://localhost:3000).
- To analyse a *remote* project, use the remote repo URL when creating a new project. If the repository is private, remember to use a personal access token as password by ticking the "Project requires authentication" box (see [How to analyse a remote repository](analyse_project.md#analyse-a-remote-repository) for more info).
- To analyse a *local* project, copy the project folder into `/arcan-trial/projects`. When creating a new project, specify the path to analyse as follows: `./projects/<folder_name>` (see [How to analyse a local repository](analyse_project.md#analyse-a-local-repository) for more info).

### Optional
Should you need to update to the latest Arcan version:

- Open the `.env` file. Change the value of the variable `ARCAN_DASHBOARD_VERSION` with the latest Arcan dashboard version tag. You can find the latest version [here](https://github.com/Arcan-Tech/arcan-2/pkgs/container/arcan-dashboard-trial).
- Change the value of the variable `ARCAN_SERVER_VERSION` with the latest Arcan server version tag. You can find the latest version [here](https://github.com/Arcan-Tech/arcan-2/pkgs/container/arcan-server-trial).
