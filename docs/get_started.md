# Get Started

## Download and Install Arcan

This is the quickstart guide to install and run the first analysis with Arcan. See the [complete reference](installation.md) for the alternative installation without Docker.

### Requirements
- Docker Engine >= 20.10 (See [https://docs.docker.com/engine/install](https://docs.docker.com/engine/install))
- Docker Compose (See [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/))

### How to run Arcan locally
1. [Clone](https://github.com/Arcan-Tech/arcan-trial) or [download](https://github.com/Arcan-Tech/arcan-trial/archive/refs/heads/main.zip) Arcan from Github. 
2. Fill in this [form](https://www.arcan.tech/on-premise-trial/). You will receive the license at the provided email address.
3. Open the email and download the attached `ArcanLicence_YYYYMMDD` licence file.
4. Copy the `ArcanLicence_YYYYMMDD` licence file to the [licences](https://github.com/Arcan-Tech/arcan-trial/tree/main/licences) directory.

### Configure the environment
1. Copy the content of the [.env.example](https://github.com/Arcan-Tech/arcan-trial/blob/main/.env.example) file into a new file named `.env`.
2. Change the value of the variable `ARCAN_LICENCE_FILENAME` with the name of licence file you copied in the [licences](https://github.com/Arcan-Tech/arcan-trial/tree/main/licences) directory.

### Run Arcan
1. To run the Arcan dashboard and the server, open your favourite terminal and navigate to the `/arcan-trial` folder. Within the folder execute: `docker compose up`.
2. You will find the dashboard at [http://localhost:3000](http://localhost:3000).

## Create and analyse a new project
Open Arcan dashboard at [http://localhost:3000](http://localhost:3000).

Click the "ADD NEW " button to analyse a new project.

1. Fill out the form on the "Add new project" page with the project's name and the programming language you want to analyse.
2. Indicate the location of the project you want to analyse:
    - To analyse a *remote* project, use the remote repo URL when creating a new project. If the repository is private, remember to use a personal access token as password by ticking the "Project requires authentication" box (see [How to analyse a remote repository](analyse_project.md#analyse-a-remote-repository) for more info).
    - To analyse a *local* project, copy the project folder into `/arcan-trial/projects`. When creating a new project, specify the path to analyse as follows: `./projects/<folder_name>` (see [How to analyse a local repository](analyse_project.md#analyse-a-local-repository) for more info).
3. In "Configure analysis" click on "ANALYSE" and then "CONTINUE" to trigger the analysis. Once the analysis is completed, you can interact with the project card on the "My projects" page.

## CI Integration

On top of running Arcan from the Dashboard, you can also attach Arcan to a Continuous Integration (CI) pipeline. For instance, you can add Arcan to your Gitlab or Github pipelines. See the [instructions](ci_integration.md) for additional details.

## Support
If you find a bug or want to suggest a new feature create a new issue on Github: [https://github.com/Arcan-Tech/arcan-issues-public](https://github.com/Arcan-Tech/arcan-issues-public).
If you  need further support or want to know more about Arcan, contact us at <info@arcan.tech> or leave a message on our [website](https://www.arcan.tech/contact/).