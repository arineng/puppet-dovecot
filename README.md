# dovecot

A fork of [https://github.com/mxhero/puppet-dovecot][1].


#### Table of Contents

1. [Module Description - What the module does and why it is useful](#module-description)
2. [Setup - The basics of getting started with dovecot](#setup)
    * [What dovecot affects](#what-dovecot-affects)
3. [Usage - Configuration options and additional functionality](#usage)


## Module Description

The dovecot module lets you use Puppet to manage the Dovecot IMAP server. This
module is developed and tested on Debian 8 but will most likely be compatible
with Debian-like distributions.


## Setup

### What dovecot affects

  * Your system's `dovecot/dovecot.conf` file.
  * Your system's `dovecot/conf.d/` directory


## Usage

  * `dovecot` : Main class
  * `dovecot::file` : Definition to manage configuration file snippets
  * `dovecot::plugin` : Definition to install plugin sub-packages


### Example Configuration

    class { 'dovecot':
        plugins                    => [ 'mysql', 'pigeonhole' ],
        protocols                  => 'imap pop3 sieve',
        verbose_proctitle          => 'yes',
        auth_include               => 'sql',
        mail_location              => 'maildir:~/Maildir',
        auth_listener_userdb_mode  => '0660',
        auth_listener_userdb_group => 'vmail',
        auth_listener_postfix      => true,
        ssl_cert                   => '/etc/pki/tls/certs/wildcard.example.com.crt',
        ssl_key                    => '/etc/pki/tls/private/wildcard.example.com.key',
        postmaster_address         => 'postmaster@example.com',
        hostname                   => 'mail.example.com',
        lda_mail_plugins           => '$mail_plugins sieve',
        auth_sql_userdb_static     => 'uid=vmail gid=vmail home=/home/vmail/%d/%n',
        log_timestamp              => '"%Y-%m-%d %H:%M:%S "',
    }

    dovecot::file { 'dovecot-sql.conf.ext':
        source => 'puppet:///modules/example/dovecot-sql.conf.ext',
    }


[1]: https://github.com/mxhero/puppet-dovecot
