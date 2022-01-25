# Introduction to Snyk Open Source Workshop

Snyk (pronounced sneak) is a developer security platform for securing code, dependencies, containers, and infrastructure as code. Snyk tests for vulnerabilities in your own code, open source dependencies, container images and infrastructure as code configurations, and offers context, prioritization, and remediation.

## What languages does Snyk support?
At the time of this workshop Snyk supports: JavaScript, Java (Gradle, Maven), .NET, Python, Golang, Swift, Objective-C (CocoaPods), Scala, Ruby, PHP, and Bazel. Learn about Snyk’s language coverage in our support documentation.

## What products and platforms does Snyk offer?
Snyk’s developer security platform integrates four key products: Snyk Open Source, Snyk Code, Snyk Container, and Snyk Infrastructure as Code (Kubernetes, Terraform, etc.).

## Which tools, IDEs, and platforms does Snyk integrate with?
Taking a developer-first approach to security, Snyk integrates with leading IDE, repository, CI/CD, runtime, registry, and issue management tools.

## How does Snyk’s security and vulnerability data compare to other vulnerability databases?
Our security intelligence database, also known as the Snyk Intel Vulnerability Database is maintained by a dedicated research team that combines public sources, contributions from the developer community, proprietary research, and machine learning to continuously adapt to the changing and expanding nature of security threats.

## Does Snyk have a CLI?
You can use the CLI for scanning and monitoring on your local machine, and integrate it into your pipeline. You can use the Snyk CLI to scan your applications, containers, and infrastructure as code for security vulnerabilities.You can install the CLI via npm, Homebrew, Scoop, or manually. Learn more in our Snyk CLI documentation.

## What we will do in this hands-on workshop?
In this hands-on workshop we will achieve the follow:
* [Step 1 Fork the highly vulnerable Goof Application](#step-1-fork-the-highly-vulnerable-goof-application)
* [Step 2 Configure GitHub Integration](#step-2-configure-gitHub-integration)
Snyk Code steps
* [Step 3 Enable Snyk Code within Snyk App](#step-3-enable-snyk-code-within-snyk-app)
* [Step 4 Add project to find Snyk Code Vulnerabilities](#step-4-add-project-to-find-snyk-code-vulnerabilities)
Snyk Open Source steps
* [Step 5 Find vulnerabilities](#step-3-find-vulnerabilities)
* [Step 6 Fix using a Pull Request](#step-4-fix-using-a-pull-request)
Snyk Container steps
* [Step 7 Find vulnerabilities in Goof’s Dockerfile](#step-5-find-vulnerabilities-in-goofs-dockerfile)
* [Step 8 Fix the Dockerfile FROM tag using a Pull Request](#step-6-fix-the-dockerfile-from-tag-using-a-pull-request)
Snyk IaC steps
* [Step 9 Find vulnerabilities in Goof’s Kubernetes yaml](#step-5-find-vulnerabilities-in-goofs-dockerfile)

## Prerequisites

* public GitHub account - http://github.com
* git CLI - https://git-scm.com/downloads
* snyk CLI - https://support.snyk.io/hc/en-us/articles/360003812538-Install-the-Snyk-CLI
* Registered account on Snyk App - http://app.snyk.io

_NOTE: Please ensure you have meet the Prerequisites prior to starting this workshop_ 

# Workshop Steps

_Note: It is assumed your using a mac for these steps but it should also work on windows or linux with some modifications to the scripts potentially_

## Step 1 Fork the highly vulnerable Goof Application

_NOTE: You may have already forked the Goopf application in that case go ahead and skip this step_

Navigate to the following GitHub repo - https://github.com/snyk/goof

* Click on the "**Fork**" button
* Ensure you are forking this repo to your public GitHub account 
* Click done

![alt tag](https://i.ibb.co/Gdf7N2W/snyk-starter-open-source-2.png)

## Step 2 Configure GitHub Integration

_NOTE: You may have already setup GitHub integration in that case go ahead and skip this step_

First we need to connect Snyk to GitHub so we can import our Repository. Do so by following these steps below:

* Login to http://app.snyk.io Sign up if you haven't already.
* Navigating to Integrations -> Source Control -> GitHub
* Fill in your Account Credentials to Connect your GitHub Account.

![alt tag](https://i.ibb.co/bPqqybM/snyk-starter-open-source-1.png)

## Step 3 Enable Snyk Code within Snyk App

* Click on the "**Settings**" button on the top most navigation bar as shown below

![alt tag](https://i.ibb.co/3fS4VCd/snyk-code-1.png)

* Click on "**Snyk Code**", then enable it and click "**Save Changes**" as shown below

![alt tag](https://i.ibb.co/bP2FpGx/snyk-code-2.png)

## Step 4 Add project to find Snyk Code Vulnerabilities

Now that Snyk is connected to your GitHub Account, import the Forked Repo "**springbootemployee-api**" into Snyk as a Project.

* Navigate to Projects
* Click "**Add Project**" then select "**GitHub**"
* Click on the Repo you forked "**springbootemployee-api**"
* Click "**Add Selected Repositories**"

![alt tag](https://i.ibb.co/TmKzh1P/snyk-code-3.png)

* Once complete you should see a "**Code Analysis**" project as shown below

_Note: There are only 2 code security issues , this is deliberate, and we will try "**Snyk Code**" on more vulnerable projects shortly_

![alt tag](https://i.ibb.co/ZfddWxb/snyk-code-4.png)

* Click on "**Code Analysis**" to view our SAST scan results

For each Vulnerability, Snyk displays the following:

1. Each Vulnerability grouped by severity
2. Each Vulnerability links to the CWE category code
3. Each Vulnerability shows the CWE category name
4. Displays the line of code where the security issue exists
5. Description for the issue and the code file name it exists in
6. A link to a Snyk Learn module on how to fix these type of vulnerabilities if available
7. The ability to ignore issues you wish to remove from the list

![alt tag](https://i.ibb.co/SJTXkDr/snyk-code-5.png)

* Click on the "**Full Details**" button as shown below

Snyk products all provide a developer-friendly experience, so Snyk Code helps developers to quickly understand the problem, learn the background, and how to approach it. Snyk Code helps you understand the dangerous code flow step-by-step. For every issue, Code also provides a link to the lines in the relevant files, to view more details on the problem like the CWE, and how to approach it.

![alt tag](https://i.ibb.co/vwxw68k/snyk-code-6.png)

* Click on "**Fix Analysis**" to see how you can fix the issue based on other open source project. On this page you get not just source code example fixes but also the following detailed information

1. Details
2. Types Of Attacks
3. Affected Environments
4. How to prevent

![alt tag](https://i.ibb.co/25P6M7g/snyk-code-7.png)

### Do you think you could fix this issue now?

Finally, if you have time go ahead and fork this repo and import this into Snyk App if you wish to see more code issues then the simple example we using here

https://github.com/papicella/goof

_Note: This may take a while as there are various other project files in this repo so you can always come back to this later to see the code results_

![alt tag](https://i.ibb.co/CJDpRys/snyk-code-10.png)

## Step 3 Find vulnerabilities

Now that Snyk is connected to your GitHub Account, import the Repo into Snyk as a Project.

* Navigate to Projects
* Click "**Add Project**" then select "**GitHub**"
* Click on the Repo you forked.

![alt tag](https://i.ibb.co/q9Rsxsh/snyk-starter-open-source-3.png)

_Note: The import can take up to one minute so you can view the import log while it's running as shown below_

![alt tag](https://i.ibb.co/RQsX6jZ/snyk-starter-open-source-14.png)

## Step 4 Fix using a Pull Request

First let's explore the Goof project risks by clicking on the "**package.json**" file which is the manifest file where the open source dependencies are declared. 

`package.json`

```json
{
  "name": "goof",
  "version": "1.0.1",
  "description": "A vulnerable todo demo application",
  "homepage": "https://snyk.io/",
  "repository": {
    "type": "git",
    "url": "https://github.com/Snyk/snyk-todo-list-demo-app/"
  },
  "scripts": {
    "start": "node app.js",
    "build": "browserify -r jquery > public/js/bundle.js",
    "cleanup": "mongo express-todo --eval 'db.todos.remove({});'",
    "test": "snyk test"
  },
  "dependencies": {
    "adm-zip": "0.4.7",
    "body-parser": "1.9.0",
    "cfenv": "^1.0.4",
    "consolidate": "0.14.5",
    "cookie-parser": "1.3.3",
    "dustjs-helpers": "1.5.0",
    "dustjs-linkedin": "2.5.0",
    "ejs": "1.0.0",
    "ejs-locals": "1.0.2",
    "errorhandler": "1.2.0",
    "express": "4.12.4",
    "express-fileupload": "0.0.5",
    "file-type": "^8.1.0",
    "humanize-ms": "1.0.1",
    "jquery": "^2.2.4",
    "lodash": "4.17.4",
    "marked": "0.3.5",
    "method-override": "latest",
    "moment": "2.15.1",
    "mongodb": "^3.5.9",
    "mongoose": "4.2.4",
    "morgan": "latest",
    "ms": "^0.7.1",
    "mysql": "^2.18.1",
    "npmconf": "0.0.24",
    "optional": "^0.1.3",
    "st": "0.2.4",
    "stream-buffers": "^3.0.1",
    "tap": "^11.1.3",
    "typeorm": "^0.2.24"
  },
  "devDependencies": {
    "browserify": "^13.1.1",
    "snyk": "^1.244.0"
  },
  "license": "Apache-2.0"
}
```
* Click on "**package.json**"

![alt tag](https://i.ibb.co/THs4g5q/snyk-starter-open-source-4.png)

For each Vulnerability, Snyk displays the following ordered by our [Proprietary Priority Score](https://snyk.io/blog/snyk-priority-score/) :
1. The module that introduced it and, in the case of transitive dependencies, its direct dependency,
1. Details on the path and proposed Remediation, as well as the specific vulnerable functions
1. Overview
1. Exploit maturity
1. Links to CWE, CVE and CVSS Score
1. Plus more ...

![alt tag](https://i.ibb.co/LYm0fVf/snyk-starter-open-source-5.png)

When using the GitHub integration, and if a fix is available, Snyk can automatically upgrade the vulnerable dependency to a non-vulnerable version through a Pull Request. 

* Click on "**Fix this vulnerability**" for "**typeorm Prototype Pollution**" issue as shown below

![alt tag](https://i.ibb.co/sRJjfnC/snyk-starter-open-source-6.png)

* On the next screen, you'll be able to confirm the issue to fix with this PR. Click "**Open a Fix PR**"

![alt tag](https://i.ibb.co/w7m8HPv/snyk-starter-open-source-7.png)
![alt tag](https://i.ibb.co/J7MmSQc/snyk-starter-open-source-8.png)

* Once it's ready, you'll be taken to the PR in GitHub, where you can review the changes in the file diff view:

Snyk integrates with your preferred Git repository to scan your manifest files for any new code and potential vulnerabilities whenever you submit a pull request (PR), protecting the security of your code before you ever merge it with the main branch

![alt tag](https://i.ibb.co/P6bcxkh/snyk-starter-open-source-9.png)

* We see that CI checks completed successfully, assuring us we didn't introduce a breaking change

![alt tag](https://i.ibb.co/SPMCMpP/snyk-starter-open-source-10.png)

* Optionally now, go ahead and merge the PR!
* Back in Snyk we can appreciate that our package.json file has 1 less High Severity Vulnerability if you did fix it


## Step 5 Find vulnerabilities in Goof’s Dockerfile

Snyk detects vulnerable base images by scanning your Dockerfile when importing a Git repository. This allows you to examine security issues before building the image, so helps solve potential problems before they land in your registry or in production.

Now that Snyk is connected to your GitHub Account, import the Repo into Snyk as a Project as this contains a Dockerfile.

* Navigate to Projects
* Click "**Add Project**" then select "**GitHub**"
* Click on the Repo "goof" that you forked earlier at Step 1.

![alt tag](https://i.ibb.co/q9Rsxsh/snyk-starter-open-source-3.png)

_Note: The import can take up to one minute, so you can view the import log while it's running as shown below_

![alt tag](https://i.ibb.co/RQsX6jZ/snyk-starter-open-source-14.png)

* Once imported you should see a reference for the Dockerfile as shown below. 

![alt tag](https://i.ibb.co/1rNMFhC/snyk-container-9.png)

* Go ahead and click on the Dockerfile this is similar to what a scan of a container from a registry looks like BUT this tim we are scanning a Dockerfile itself versus the full container image.

In a Dockerfile project, you can find the relevant metadata of the Dockerfile and the base image used. If the base image is an [Official Docker image](https://docs.docker.com/docker-hub/official_images/), the results include recommendations for upgrades to resolve some of the discovered vulnerabilities

## Step 6 Fix the Dockerfile FROM tag using a Pull Request

Here we will go ahead and fix our Dockerfile using the "**Open a Fix PR**" button as follows:

* Click on "**Open a Fix PR**" for the base image "**node:16.6.0-slim**" as per below

![alt tag](https://i.ibb.co/5kY26FR/snyk-container-13.png)

* Click on "**Open a Fix PR**" on the resulting page as shown below

![alt tag](https://i.ibb.co/C0tn01C/snyk-container-14.png)

* A PR is then created as show below. "**Files Changed**" will show you what it's updating in the Dockerfile itself

![alt tag](https://i.ibb.co/py4GdJS/snyk-container-15.png)

* Click on "**Merge Pull Request**" button as shown below

![alt tag](https://i.ibb.co/hCwDCFP/snyk-container-16.png)

* Return to the projects dashboard and you will see a new scan has occurred automatically and now our Dockerfile shows much less issues than previously. Of course until we build a new container and add it to the registry the container itself will still have the old base image in place.

![alt tag](https://i.ibb.co/pbqmR1v/snyk-container-17.png)
