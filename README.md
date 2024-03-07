# Ansible playbook: labocbz.deploy_nextcloud

![Licence Status](https://img.shields.io/badge/licence-MIT-brightgreen)
![CI Status](https://img.shields.io/badge/CI-success-brightgreen)
![Testing Method](https://img.shields.io/badge/Testing%20Method-Ansible%20Molecule-blueviolet)
![Testing Driver](https://img.shields.io/badge/Testing%20Driver-docker-blueviolet)
![Language Status](https://img.shields.io/badge/language-Ansible-red)
![Compagny](https://img.shields.io/badge/Compagny-Labo--CBZ-blue)
![Author](https://img.shields.io/badge/Author-Lord%20Robin%20Crombez-blue)

## Description

![Tag: Ansible](https://img.shields.io/badge/Tech-Ansible-orange)
![Tag: Debian](https://img.shields.io/badge/Tech-Debian-orange)
![Tag: Docker](https://img.shields.io/badge/Tech-Docker-orange)
![Tag: Nexcloud](https://img.shields.io/badge/Tech-Nexcloud-orange)
![Tag: SSL/TLS](https://img.shields.io/badge/Tech-SSL%2FTLS-orange)
![Tag: Apache2](https://img.shields.io/badge/Tech-Apache2-orange)
![Tag: PHP](https://img.shields.io/badge/Tech-PHP-orange)
![Tag: PHP-FPM](https://img.shields.io/badge/Tech-PHP--FPM-orange)

An Ansible playbook to deploy and configure a Nexcloud server on your hosts.

This Ansible playbook orchestrates the seamless deployment of Nextcloud, a powerful and versatile self-hosted file sync and sharing platform. The playbook ensures the installation of Nextcloud in a specified version on the server, leveraging archive downloads and deployment to the designated location.

To provide secure access to the Nextcloud interface, Apache2 is installed and configured as a reverse proxy with SSL/TLS support. This setup ensures encrypted communication channels, safeguarding sensitive data and user information. Additionally, robust security measures, including Web Application Firewall (WAF), Quality of Service (QoS), and other tools, are installed to enhance the overall security posture of the deployment.

Given that Nextcloud is a PHP-based application, PHP is installed along with PHP FastCGI Process Manager (FPM). A specific PHP pool is created to optimize performance and resource utilization for Nextcloud operations. While the creation of the database is not handled by this playbook, it manages the migration and installation of data, including population with embedded SQL scripts provided by Nextcloud.

Although Redis can be utilized to further optimize Nextcloud performance, its installation is not managed by this playbook. However, the playbook is designed to seamlessly integrate with existing Redis setups if desired.

Overall, this playbook offers a comprehensive solution for deploying Nextcloud with security, performance, and scalability in mind. By automating the installation and configuration process, organizations can quickly and efficiently set up their own Nextcloud instances, empowering users with a secure and reliable file sync and sharing solution.

## Deployment diagramm

![Ansible-Playbook-Labocbz-Deploy-Nextcloud](./assets/Ansible-Playbook-Labocbz-Deploy-Nextcloud.drawio.svg)

In this potential deployment scenario orchestrated by the playbook, we envision a robust architecture comprising several interconnected components to facilitate the deployment of Nextcloud.

At the heart of the deployment is the Nextcloud application, installed on a designated server. Nextcloud is hosted within the server environment, managed through archive downloads and deployed to the specified location. Additionally, PHP and PHP FastCGI Process Manager (FPM) are installed to support Nextcloud's PHP-based infrastructure.

To provide secure access to the Nextcloud interface, Apache2 is installed and configured as a reverse proxy with SSL/TLS support. This setup ensures encrypted communication channels, allowing users to securely access Nextcloud's features and functionalities.

Robust security measures, including Web Application Firewall (WAF), Quality of Service (QoS), and other tools, are integrated into the deployment architecture to enhance the overall security posture of the Nextcloud environment.

While the creation of the database is not handled by this playbook, the migration and installation of data are managed seamlessly. Nextcloud's embedded SQL scripts are utilized to populate the database with the necessary information, ensuring a smooth and efficient deployment process.

Although Redis can be utilized to optimize Nextcloud performance, its installation is not managed by this playbook. However, the architecture is designed to seamlessly integrate with existing Redis setups if desired.

Overall, this deployment architecture offers a comprehensive and secure solution for deploying Nextcloud, empowering organizations with a reliable and efficient file sync and sharing platform. Through automation and integration of essential components, users can quickly and easily set up their Nextcloud instances while ensuring high performance, scalability, and security.

## Tests and simulations

### Basics

You have to run multiples tests. *tests with an # are mandatory*

```MARKDOWN
# lint
# syntax
# converge
# idempotence
# verify
side_effect
```

Executing theses test in this order is called a "scenario" and Molecule can handle them.

Molecule use Ansible and pre configured playbook to create containers, prepare them, converge (run the playbook) and verify its execution.
You can manage multiples scenario with multiples tests in order to get a 100% code coverage.

This playbook contains a ./tests folder. In this folder you can use the inventory or the tower folder to create a simualtion of a real inventory and a real AWX / Tower job execution.

### Command reminder

```SHELL
# Check your YAML syntax
yamllint -c ./.yamllint .

# Check your Ansible syntax and code security
ansible-lint --config=./.ansible-lint .

# Execute and test your playbook
molecule lint
molecule create
molecule list
molecule converge
molecule verify
molecule destroy

# Execute all previous task in one single command
molecule test
```

## Installation

To install this playbook, just copy/import this playbook or raw file into your fresh playbook repository or call it with the "include_playbook/import_playbook" module.

## Usage

### Vars

```YAML
# From inventory
---
# all vars from to put/from your inventory
# see tests/inventory/group_var for all groups and vars.
```

```YAML
# From AWX / Tower
---
all vars from to put/from AWX / Tower
```

## Architectural Decisions Records

Here you can put your change to keep a trace of your work and decisions.

### 2024-01-18: First Init

* First init of this playbook with the bootstrap_playbook playbook by Lord Robin Crombez

## Authors

* Lord Robin Crombez

## Sources

* [Ansible playbook documentation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_playbooks.html)
* [Ansible Molecule documentation](https://molecule.readthedocs.io/)
