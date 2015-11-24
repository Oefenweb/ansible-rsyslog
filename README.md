## rsyslog

[![Build Status](https://travis-ci.org/Oefenweb/ansible-rsyslog.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-rsyslog) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-rsyslog-blue.svg)](https://galaxy.ansible.com/list#/roles/6175)

Manage rsyslog and rsyslog.d in Debian-like systems.

#### Requirements

None

#### Variables

* `rsyslog_repeated_msg_reduction`: [default: `true`]: Repeated message reduction 
* `rsyslog_file_owner`: [default: `syslog`, `root` on Debian]: Set the file owner for dynaFiles newly created
* `rsyslog_file_group`: [default: `adm`]: Set the file group for dynaFiles newly created
* `rsyslog_file_create_mode`: [default: `0640`]: The creation mode with which rsyslogd creates new files
* `rsyslog_dir_create_mode`: [default: `0755`]: The creation mode with which rsyslogd creates new directories 
* `rsyslog_umask`: [default: `0022`]: The default rsyslogd processes' umask
* `rsyslog_priv_drop_to_user`: [default: `syslog`, not used on Debian]: Name of the user rsyslog should run under after startup
* `rsyslog_priv_drop_to_group`: [default: `syslog`, not used on Debian]: Name of the group rsyslog should run under after startup

* `rsyslog_rsyslog_d_files` [default: `{}`]: `/etc/rsyslog.d/*` file(s) declarations
* `rsyslog_rsyslog_d_files.key`: The name of the rsyslog configuration file (e.g `50-default`)
* `rsyslog_rsyslog_d_files.key.{n}.rule` [required]: 
* `rsyslog_rsyslog_d_files.key.{n}.logpath` [required]: 

## Dependencies

None

#### Example(s)

##### Simple configuration

```yaml
---
- hosts: all
  roles:
    - rsyslog
```

##### Complex configuration

```yaml
---
- hosts: all
  roles:
    - rsyslog
  vars:
    rsyslog_repeated_msg_reduction: true
    rsyslog_file_owner: syslog
    rsyslog_file_group: adm
    rsyslog_file_create_mode: '0640'
    rsyslog_dir_create_mode: '0755'
    rsyslog_umask: '0022'
    rsyslog_priv_drop_to_user: syslog
    rsyslog_priv_drop_to_group: syslog
    rsyslog_rsyslog_d_files:
      20-ufw:
        - rule: ':msg,contains,"[UFW "'
          logpath: '/var/log/ufw.log'
```

#### License

MIT

#### Author Information

* Mark van Driel
* Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-rsyslog/issues)!
