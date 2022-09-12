# CI/CD
A development methodology and set of practices that allows for a consistent and automated way of building, packaging and testing applications.
CI (Continuous Integration) - verification of the program (for example, the compilation of JS, PHP modules, and automated tests).
CD (Continuous Delivery) - deployment of the application to the server (updating changed files on the server, assembling JS, PHP modules, conducting migrations (example for laravel)).
You can read more in Google by choosing a direction, for example CI/CD for JS developers, or for PHP, etc.

---

## 1. Bitbucket setup
1. Open in an existing project **"Repository settings"**.
2. In the section **"PIPELINES"** choose **"Settings"** and activate **"Enable Pipelines"**.
3. Choose **"SSH keys"** and generate or add existing keys (they will be needed for CD, update deployment on the server, i.e. these keys must be on the server)

---

## 2. File configuration bitbucket-pipelines.yml
1. Create a file in the root of the repository **bitbucket-pipelines.yml**.
2. To start, add the code given in the file **[bitbucket-pipelines.yml](bitbucket-pipelines.yml)**.
3. Check out the documentation **[examples of configuring the file](https://support.atlassian.com/bitbucket-cloud/docs/configure-bitbucket-pipelinesyml/)** and make necessary changes for the current project.

---
## 3. Recommendations for setting
1. Try to move long sequences of commands to external files as much as possible to make the bitbucket-pipelines.yml configuration file shorter and easier to understand for other developers on the team.
2. First configure the project locally in **docker**, and then deploy it in the bitbucket environment already with docker-compose.yml to start the test build and automatic tests (CI). Pipelines have a docker extension to work with similar projects. This will allow you not to specify a series of commands to install linux applications necessary for the project to work.
3. For CD, use **.sh** files on the server (script that allow you to run the necessary commands). In this way, it will be possible to call the necessary script in one line in the bitbucket-pipelines.yml file, which will already contain all the necessary commands for deployment.
