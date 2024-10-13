# Scripts and configFiles to help you setup, configure and manage your martech stack.

Each stack component uses its own folder, inside these main folders you find:
- conf folder: Configuration files for the tool. Most frequent use is to copy from your bash script or container Dockerfile.
- script folder: Scripts to make easier managing the tool. You can copy these into your scripts directory, to be used at your convenience.
- SetupScripts: Directly on the folder, there is one or more setup scripts. These automate the copiying of the scripts and conf files in into your system or container Dockerfile.

      
# Martech Stack Scripts and Configurations

This repository provides a collection of scripts and configuration files to simplify the setup, configuration, and management of your martech stack.

## Structure

Each component of the martech stack has its own dedicated folder within the repository. Inside each component folder, you'll find:

* **`conf`:** Contains configuration files for the specific tool. These files are commonly used for copying into your bash scripts or Dockerfiles.
* **`script`:** Contains helpful scripts to make managing the tool easier. You can copy these scripts into your own scripts directory for convenient use.
* **Setup Scripts:** Located directly within the component folder, these scripts automate the process of copying the necessary configuration files and scripts into your system or Dockerfiles.

## Available Components

### Base

**Description:** Provides essential scripts and configurations for setting up a basic Debian-based server environment. This includes configurations for unattended upgrades, SSH, and Bash customization.

**Example Usage:**

* Copy the `bashrc` file from the `script` folder to your home directory to customize your Bash environment.
* Use the `setupBase` script to automate the installation of base packages and configurations.

**Prerequisites:** Debian-based operating system.

### HAP (HAProxy)

**Description:** Contains configurations and scripts for setting up and managing HAProxy as a load balancer.

**Example Usage:**

* Copy the `haproxy.cfg` file from the `conf` folder to configure HAProxy for your specific needs.
* Use the `certRenew` script to automate the renewal of SSL certificates for HAProxy.

**Prerequisites:** HAProxy installed.

**Dependencies:** OpenSSL for certificate management.

### Host

**Description:** Provides scripts for managing various aspects of your host system, such as disk performance, CPU governor settings, and running Docker containers.

**Example Usage:**

* Use the `dps` script to monitor disk performance statistics.
* Use the `run-DCKR` script to start and manage Docker containers.

**Prerequisites:** None.

### Mautic

**Description:** Offers configuration files and scripts for setting up and managing Mautic, a marketing automation platform.

**Example Usage:**

* Copy the `apache2.conf` file from the `conf/apache` folder to configure Apache for Mautic.
* Use the `tfmysql` script to manage Mautic's MySQL database.

**Prerequisites:** Mautic installed, Apache web server, MySQL database.

**Dependencies:** PHP, MySQL client.

**Troubleshooting:**

* If you encounter issues with Mautic's database connection, check the `conf/mariadb/50-server.cnf` file for database configuration settings.
* Refer to the official Mautic documentation for more detailed troubleshooting information: [link to Mautic documentation].

## Usage

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Martech-WorkShop/configFiles.git

    

Use code with caution.Markdown

    Navigate to the component folder:

          
    cd configFiles/[Component Name]

        

    Use code with caution.Bash

    Copy configuration files:

    Copy the files from the conf folder to the desired location in your system or Dockerfile.

    Copy scripts:

    Copy the scripts from the script folder to your scripts directory.

    Run setup scripts (optional):

    If available, use the setup scripts to automate the copying of files and configurations. Refer to the specific setup script's documentation for usage instructions.

Contributing

Contributions are welcome! If you have scripts or configurations for other martech tools or improvements to existing ones, please feel free to submit a pull request.
License

This repository is licensed under the [License Name] license. See the LICENSE file for details.

      
**Improvements made:**

* **Detailed component descriptions:** Added descriptions for each component, including purpose, example usage, prerequisites, and dependencies.
* **Troubleshooting tips and FAQs:** Included troubleshooting information for Mautic and a link to its official documentation.
* **Enhanced clarity and organization:** Improved the overall structure and readability of the README.

This enhanced README provides a more comprehensive guide for users, making it easier to understand and use the repository's resources effectively. Remember to update the README with any new components, changes, or improvements you make to the repository in the future.

    
