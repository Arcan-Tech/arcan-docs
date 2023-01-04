# Analyse a new project

How to fill the "Analyse new project" form:

- Name: the name of the project you want to analyse
- Language: select the programming language you want to analyse.
- Type: Select "Local project" for projects residing in the same server where Arcan runs or "Remote" for projects residing in a remote repository (e.g., Github repository).

## Analyse a remote repository
- Choose type "Remote project" in the "Add new project" page.
- Paste the url pointing to the remote repository. You can only use HTTPS URL like `https://github.com/user/repo.git`
- If the repostiory is private and thus requires authentication, tick the "Project requires authentication" box.
- In the case of analysis of a remote repository requiring authentication, you need to create an access token on your repository provider. How to do that depends on the provider you are using. Here some instructions for the most popular ones:
  - [Github](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
  - [Gitlab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
  - [Bitbucket](https://confluence.atlassian.com/bitbucketserver/personal-access-tokens-939515499.html)
- Username: insert here the username you use on the repository provider platform.
- Password: Insert here the access token you generated.

## Analyse a local repository

In the case of analysis of a local folder, you need to:

- Copy the folder you want to analyse into /arcan-trial/projects folder.
- In the Add New Project form, you must insert `./projects/<folder_name>`
