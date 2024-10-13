# Scripts and configFiles to help you setup, configure and manage your martech stack.


### What is inside this repo?
configFiles: Configuration files for popular Martech software and for the services required to run these.
helperTools: Little scripts (akin to aliases) aimed at facilitating sytem and tooling administration and troubleshooting.
setupScripts: Scripts to automate the deployment of configFiles and helperTools.

Each stack component uses its own folder, inside these main folders you find:
- conf folder: Configuration files for the tool. Most frequent use is to copy from your bash script or container Dockerfile.
- script folder: Scripts to make easier managing the tool. You can copy these into your scripts directory, to be used at your convenience.
- SetupScripts: Directly on the folder, there is one or more setup scripts. These automate the copiying of the scripts and configFiles in into your system or Dockerfile.

      
# Martech stack scripts, configFiles and automations
### This repository provides a collection of scripts and configFiles files to simplify the setup, configuration, and management of your martech stack.

### What is what
setupScripts are meant to just move files around and assign permissions.
setupScripts are NOT supposed to execute any code beyond that, to keep them as unopinionated as possible.
Custom logic and more complex steps can be added as general Scripts.
The main intent is for logic to be added on Dockerfiles while keeping setupScripts inert and unopinionated.

Currently, there can be some additional steps executing some task. However, any bash commands, other than those required to copy files should not be included in the a setupScript and any current ocurrence will be removed over time.


## Structure

Each component of the martech stack has its own folder. Inside each component's folder, you'll find:

* **`conf`:** Configuration files for the tool. Copy these to your system with your bash scripts or Dockerfiles or just download when required.
* **`script`:** Scripts to make managing the tool easier. Copy these scripts into your scripts directory for later convenient use.
* **Setup Scripts:** Located directly in each tool's root folder, these scripts "install" all the scripts and config files onto your system or container.

Assumptions:
While all these scripts are just regular bash scripts and can be run and used on any Linux environment:
- Supported OS: Debian 12-slim. We only have the bandwith to support one OS right now, currently this is Debian 12-slim only.
- Ontended use: The intended use and aim is to simplify Dockerfile creation. Instead of using COPY from local files, you can reference the files on this repository.
- The scripts are tested for Bash, not sh, not zhs, etc. They will probably work just fine on those shells too, we just can't support all of the shells right now.
-  


### Usage

This is NOT an application. This is meant as a file hosting repo.
Download any singular script or configFile you want to use in your own project, for example with wget or curl.
Use our setup scripts to automate copying, permissions, etc...
Or build your own setupScript, which can pick and choose any of our scripts and configFiles to create your Dockerfile.

Most habitual use case:

Call a setupScript: Effectively copy a setupScript from this repo to your system or Dockerfile and then run it.
wget : scriptname
bash scriptname

The setupScript will download all the files pertaining to the specific tool.
It will move the configFiles to each proper location (path) expected by each tool.
Move any tooling scripts to the /usr/local/bin.
Then assign permissions to the scripts.
Delete itself.


## Branches:
Feature branches will be created upon request, for major tool version revamps.
Bugfix and hotfix branches are created as needed, tho we rarely have any.
Dev Is where other development branches like Feature, Bugfix, etc. are merged.
Stage is where the different versions are published. 
Prod is the "main / master" contains the latest production-ready version.
LTS for those extra carefull people who can not risk it with mere "production-ready" files.
v6, v7, v8, etc... These are frozen in time and allow you to use the same version forever...

## Which branch shoulkd I use?
If you don't know which branch is best for you:
Start with Prod, it's up-to-date enough for your scripts not to go outdated, but far from cutting edge, so you do not hit any trouble.
LTS is even more conservative and further away from the latest stuff, making it more resillient, but still "getting updates automatically".
Add and forget: Both Prod and LTS can be used in your production-ready Dockerfile or script, they will get updates over time so your Dockerfile definitions won't get outdated, in other words you will be using v6 until v7 reaches matturity and then it will be used on your Dockerfile automatically over time to v7, v8, etc... so you don't have to revise these manually.
But, if you want absolute zero chances of trouble, ever, consider using named versions, like v6,v7,etc, these won't change ever, because of that, you will have to deal with any eventual updates manually.

ATTENTION: ALL CURRENT VERSIONS ARE UNSTABLE. This repository is fairly new, and every branch is now on v6, including Prod and LTS, not because they are mature enough, not because v6 is heavily tested, but because v6 is the only existing version and there isn't any other version available, yet. Use with caution!


## Contributions are very welcome.

If you found this repo to be usefuyl to you, or you have ideas on how to make it better for everyone, consider contributing.
Contributing can be as simple as reporting a typo or as complex as writing all the configFiles, helperTools and setupScripts for a new Martech tool.

Start small, see how you like it, take more responsibility whenever you feel like so.
- Share an idea in the forum or the projects.
- Add a new entry on the Wiki.
- Create an Issue for a bug fix or an improvement.
- File a PR with an improved comment or for adding a comment where there is none.

Non-coding things we need help with:
- The "Getting started" wiki: A hands-on version of this readme, with more examples.
- More complex use cases that go beyond mere examples.
- Success histories: How did this repo help you?
- Triage and moderation.

For Sysadmins, DevOps, Bash wizards and Dockerfile maestros:
- If you have created scripts or have great configuration files for other martech tools, use this repo to share with the world.
- If you have improvements or simply comments about how to improve the existing scripts and files, considering opening an issue or filing a PR.

## License:
This repository is licensed under the [License Name] license. See the LICENSE file for details.



## Currently Available Components

### Base

**Description:** Files for a basic, unopinionated Debian-Slim environment.
Used while Building a "Base" Dockerfile, the resulting image would contain the common tools required to "enrich" a slim-based container image.
This includes configurations for unattended upgrades, SSH, and some Bash customization.

**Example Usage:**

* Copy the `bashrc` file from the `script` folder to your home directory to customize your Bash environment.
* Use the `setupBase` script to automate the installation of base packages and configurations.


### HAP (HAProxy)

**Description:** Scripts and configFiles for setting up and managing HAProxy as a reverse proxy or load balancer.
Used while Building an HAproxy Dockerfile, the resulting image would contain the basics to get started using HAP.
This includes scripts to manage SSL certificates and a basic, initial configuration file to get started with.

**Example Usage:**

* Copy the `haproxy.cfg` file from the `conf` folder to configure HAProxy for your specific needs.
* Use the `certRenew` script to automate the renewal of SSL certificates for HAProxy.

**Prerequisites:** HAProxy installed.

**Dependencies:** Assumes building from a "Base" container, otherwise call the setupBase script before using the setupHAP script.
OpenSSL for certificate management.


### Host

**Description:** Scripts and configFiles for setting up and managing your host system, like CPU governor settings, and setting up Docker or LXD.


**Example Usage:**

* Use the `dps` script to monitor disk performance statistics.
* Use the `run-DCKR` script to start and manage Docker containers.

**Prerequisites:** Debian 12 OS.
Maybe the only script that does NOT assume creation from "Base"
It will work on any KVM-Based VPS, but the target is virtualizing Bare-metal servers and building clusters of bare-metal servers.


### Mautic: Marketing Automation

**Description:** Scripts and configFiles for setting up and managing your Mautic server or VPS.

**Example Usage:**

* Copy the `apache2.conf` file from the `conf/apache` folder to configure Apache for Mautic.
* Use the `tfmysql` script for troubleshooting, by checking your MySQL database error logs.

**Prerequisites:** Mautic installed, Apache web server, MySQL database.

**Dependencies:** Mautic, Apache2, PHP-FPM, MariaDB.
