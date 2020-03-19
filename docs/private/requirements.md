# Requirements

The private scraper has a few general requirements in order to properly run.

### General Requirements

 - Server/machine with the ability to connect to your git hosting service.
 - Administration access into Git service to create access tokens or app passwords.
   - (NOTE: The account associated with the token/password should have permissions to access all relevant repositories)
 - Network capable of allowing clients to connect to server/machine hosting the private scraper.

### Network Requirements

 - Static IP address or ability to set up dynamic dns.
   - Non-static ip addresses can be used but this may cause issues with the clients ability to connect without frequent alterations to the client configuration file.

### System Requirements (Docker-Deployment)

 - Windows 10 Pro, Enterprise, and Education
 - MacOS
 - Linux (CentOS, Ubuntu, or Red Hat Enterprise Linux 7 (RHEL7) with kernel version 3.10 or higher)
 - Recommended 2 GB of RAM
 - Recommended 5 GB of available disk space