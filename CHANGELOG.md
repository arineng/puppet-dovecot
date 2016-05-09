## Release 0.2.0
### Summary

Forked from https://github.com/mxhero/puppet-dovecot.

#### Features

- Allow 15-mailboxes.conf to be excluded. Steven Bambling <smbambling@gmail.com>
- Quota rules and quote-status service.
- Add parameter auth_passwdfile_userdb_driver.
- Add directives for unix_listener auth-master.
- Add directives {first|last}_valid_guid.

#### Improvments

- Align templates with Debian Jessie (dovecot-core_2.2.13-12-deb8u1).
- Conform with Puppet coding style guide.
- Delete original configuration files that templates were based on.
