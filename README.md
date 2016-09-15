# New Relic PHP Agent

Sets up New Relic PHP agent: https://docs.newrelic.com/docs/php/new-relic-for-php

## Requirements

Debian Wheezy, with PHP installed. This role tries to restart PHP-FPM and Nginx.

## Role Variables

The variables that can be passed to this role and a brief description about them are as follows

    # License key (required)
    newrelic_license_key: ab2fa361cd4d0d373833cad619d7bcc424d27c16

    # Application name (required)
    newrelic_appname: myapp-host1;myapp

# Dependencies

Requires the New Relic repository to be set up; depends on [ansible-newrelic](https://github.com/FloeDesignTechnologies/ansible-newrelic) for this purpose.

## Examples

### Paramaterized Role

    ---
    - hosts: all
      roles:
        - { role: chriskite.newrelic, newrelic_license_key: ab2fa361cd4d0d373833cad619d7bcc424d27c16, newrelic_appname: myapp-host1;myapp }

### Vars

    ---
    - hosts: all
      vars:
        newrelic_license_key: ab2fa361cd4d0d373833cad619d7bcc424d27c16
        newrelic_appname: myapp-host1;myapp
      roles:
        - chriskite.newrelic-php

### Group vars

#### group_vars/production

    ---
    newrelic_license_key: ab2fa361cd4d0d373833cad619d7bcc424d27c16
    newrelic_appname: myapp-host1;myapp

#### site.yml

    ---
    - hosts: all
      roles:
        - newrelic-php
