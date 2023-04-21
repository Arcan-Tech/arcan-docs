---
title: Common issues & solutions


---
# Common issues & solutions

## Analysis never completes / hangs
If you successfully added the project, started the analysis, but the dashboard keeps showing the spinning circle on your project, then it is likely that your analysis is hanging indefinitely.
To check whether this is the case, close the dashboard and look at the server's logs (`docker logs -f arcan-trial-arcan-server-1`).
Are there any logs that indicate progress? If all you see is `Quartz`-related logs and memory logs, then it is likely the analysis is stuck.

This could be caused by any of these:

- You configured the analysis to analyse too many commits, namely, you set a wide timespan for the analysis (e.g. 10 years) and a low interval between commits (`<30`). If this is the case, you should restart the server, delete the project, and re-run the analysis with a higher interval between commits (`>60`). Alternatively, try running a snapshot (non-historical) analysis.
- You are running Arcan on an ARM processor (e.g. M1 Mac).
Unfortunately, the dockerized version of Arcan does not support ARM processor architecture. The solution is to either run it on a supported processor architecture (i.e. x86/x64) or contact our support (see below).
- Arcan does not have sufficient memory. This is likely if you are trying to analyse a large project (250+ KLOC). You can try setting the environment variable `SERVER_JVM_MEMORY` to `16G` in the `docker-compose.yml` file.
- You are running Docker on a Windows host machine. Unfortunately, Docker on Windows is not as optimized as Windows on *nix OSs, therefore, if you are trying to analyse large projects, you should consider using a *nix OS.

## Empty project (no metrics)
If your project has no smells and/or the number of lines of code is 0 (i.e. KLOC), then it's likely that the analysis has not completed successfully. 
Another symptom is that your project has an *unexpected* `A` rating.

This problem may arise because of the following causes:

- You are analysing a Python project. Python is not yet fully supported and therefore there might be some projects/python features that are not yet fully supported, or handled correctly.
- You are trying to analyse a "Local project" and may have mispelled the path. Delete the project, create a new one, and ensure that the path is correctly spelled as `./projects/<FOLDER_NAME>`. Note the `.` at the beginning of the path. If you added the project correctly, you should be able to see the directory tree of the project after the project was created. Alternatively, consider using the "Upload zip" feature (available as of `2.8.5-RELEASE`).
- You are analysing a large project and the analysis has failed silently. In this case, try following the steps mentioned above in the "Analysis never completes" section.

## Cannot add a project
If you cannot add to Arcan your project, then it might be because:

- You are trying to add a remote project but the URL or credentials are incorrect. If so, Arcan shows an error message that tells you which is the case (wrong credentials or wrong URL). Note that GitHub and GitLab do not support password authentication any longer in favor of Private Access Token (PAT). Please refer to [GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)'s and [GitLab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)'s support pages on how to solve this problem. In both cases, to authenticate, you should paste the PAT in the Arcan's password field.
- You are trying to connect to a non-supported remote (Git incompatible). Arcan only supports the Git version control system, thus, if you want to analyse a non-Git project, you must download it on your local machine and either upload it as a zip, or use the "Local project" feature. Note that **historical analysis is not supported** in this case.
- You get the error `Connection refused. Upload size may exceed server's limit.`. In this case, it means you have to increase the allowed maximum size of uploads. To do so, change/add to the `docker-compose.yml` file, the following variable `SERVER_MAX_UPLOAD_SIZE: 500MB`, or whatever value you fancy.
- When adding a new project, the dropdown menu to select the programming language is empty. This is always caused by the fact that the dashboard cannot communicate with the server. Usually, this happens because you have installed Arcan on a remote machine (e.g., a virtual machine on a shared server) and use the dashboard from your local machine. By default, Arcan dashboard tries to reach the server at `localhost:8080` but the server is not running on your machine. To fix the problem, open `docker-compose.yml` and modify `REACT_APP_GRAPHQL_SERVER_URL` and `REACT_APP_PUBLIC_URL`  by replacing localhost with the IP address of your machine.

## Some information is missing from the Dependency Graph

If the reverse engineering of dependencies looks incomplete and you think the analysis does not return the expected results, it might be due to the programming language under analysis. Check our compatibility page to verify Arcan's supported languages and consult our tips for specific language frameworks (e.g., Spring).


# Can't solve a problem?

Should you encounter a different problem, or you cannot solve any of the problems listed above, please consider [opening an issue](https://github.com/Arcan-Tech/arcan-issues-public/issues/new/choose).

# Need more help?

Feel free to contact our support team at <support@arcan.tech> or write us on [Discord](https://discord.gg/Nfk7juy3qd).
