# wilmardo.nrpe-client

[![Build Status](https://travis-ci.org/wilmardo/ansible-role-domoticz.svg?branch=master)](https://travis-ci.org/wilmardo/ansible-role-domoticz)
[![Galaxy](https://img.shields.io/badge/galaxy-wilmardo.domoticz-blue.svg)](https://galaxy.ansible.com/wilmardo/domoticz/)

This role installs the NRPE client on a monitoring server. You can use this role as an addon to the [wilmardo/nagios](https://galaxy.ansible.com/wilmardo/nagios/) role.

## Requirements

None.

## Role Variables

### Default usage

As default Domoticz is installed and running http on port 8080 and https on port 8081 with the default certificate. 
If you want to adapt this to your needs look at the [Advanced usage](#advanced-usage) section.

### Advanced usage

For more advanced usage the following variables are available:
```yaml
# The directory where the downloaded files will be placed
domoticz_download_dir: "/home/domoticz"

# The Domoticz download url
domoticz_url: "https://releases.domoticz.com/releases/release/domoticz_linux_x86_64.tgz"
# The name of the untarred Domoticz directory
domoticz_src: "domoticz"

# The user which the Domoticz daemon runs as
domoticz_user: domoticz
# The group which the Domoticz daemon runs as
domoticz_group: domoticz
# The port for Domoticz to run http (-www daemon option). For ports <1024 root privileges are required, better to setup a reverse proxy with for example Nginx
domoticz_port: 8080
# Enable/Disable https for Domoticz
domoticz_https: yes
# The port for Domoticz to run https (-sslwww daemon option). For ports <1024 root privileges are required, better to setup a reverse proxy with for example Nginx
domoticz_https_port: 8081
# Path to SSL certificate, if left default the server_cert.pem from Domoticz will be used (-sslcert daemon option)
domoticz_ssl_cert: "{{ domoticz_download_dir }}/{{ domoticz_src }}/server_cert.pem"

# Add support for ZWave
domoticz_zwave_support: no
# The version of Open-ZWave to be installed (accepts same arguments as version parameter of git module)
zwave_version: master
# The Open-ZWave git url
zwave_url: "https://github.com/OpenZWave/open-zwave.git"
```

## Dependencies

None

## Example Playbook

Install Domoticz with the default settings
```yaml
- hosts: monitoring-servers
  roles:
     - { role: wilmardo.domoticz }
```
After running the playbook Domoticz can be found at http://ipaddress:8080 and https://ipaddress:8081

## License

BSD-3-Clause-Clear

## Author Information

This role was created in 2017 by [Wilmar den Ouden](https://wilmardenouden.nl).
