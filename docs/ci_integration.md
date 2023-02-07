# CI Integration

On top of running Arcan from the [Dashboard](installation.md), you can also attach Arcan to a Continuous Integration (CI) pipeline.

Arcan offers a command line interface (CLI) that can be invoked from your CI pipeline and save the results on a remote database that can later be accessed through the dashboard to inspect the results.

Below you will find the instructions on how to set up a CI pipeline that runs Arcan on the current commit.
We provide a set of convenience scripts to make this job easier (write us an [email!](mailto:info@arcan.tech)).

!!! warning 

    Notice that this feature is not directly available in the 30-day free trial, you must request it on our [website](https://www.arcan.tech/contact/) or by sending us an [email](mailto:info@arcan.tech).

## Instructions

### Requirements:
- The Arcan CLI Jar (or Docker image) available on the CI runner machine
- Access to the source code (to do the analysis)
- Network access to the database the dashboard is connected to (to save the results)

### Step 1: Configure the analysis

First, generate the analysis configuration:

```bash
cd arcan-ci
./analyse-configs/mkconfig.sh ${PROJECT_NAME}
```

Then proceed editing the generated files accoding to your preference:

```bash
vim ./analyse-configs/${PROJECT}/descriptor.yml
vim ./analyse-configs/${PROJECT}/source-filters.yml 
```

Next, configure the connection to the results database by changing the following variables in `run-arcan.sh`:

```
JDBC_URL=arcan-postgres:5432/arcan
JDBC_USERNAME=username
JDBC_PASSWORD=password
```

### Step 2: Attach the runner to your pipeline

Add the following lines to your pipeline

```bash
./run-arcan.sh analyse path/to/project $LANGUAGE
```
The script `./run-arcan.sh` is the main file of the repository that automates all the execution of a PoC.