Dokuwiki
========

A role that installs Dokuwiki for an nginx/letsencrypt setup.

Requirements
------------

- LetsEncrypt
- Nginx

Role Variables
--------------

- `dokuwiki_source` Archive to grab the source code version. Defaults to the
  officiel latest stable release.
- `dokuwiki_install` Installation mode, gives access to the `/setup.php` file
  for first time run. Defaults to true. Be sure to set it to false once
  installed.

- `dokuwiki_base` Where to put Dokuwiki. Defaults to `/var/www/dokuwiki`.

- `dokuwiki_group` Group for the Dokuwiki files. Defaults to `www-data`.
- `dokuwiki_user` User for the Dokuwiki files. Defaults to `dokuwiki`.

- `nginx_server_name` Host name for nginx. Defaults to `dokuwiki.localhost`.
- `nginx_filename` Nginx fie name. Defaults to `dokuwiki-{{ nginx_server_name
  }}`

- `letsencrypt_wellknown` Location of the letsencrypt .wellknown directory.
  Defaults to `/var/www/letsencrypt`.
- `letsencrypt_activate` Activate the LetsEncrypt support
- `letsencrypt_https` Serve HTTPS only once LetsEncrypt is ready.
- `letsencrypt_domain` Name for the certificate to search for. Defaults to the
  nginx server name.

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: MicroJoe.dokuwiki
          dokuwiki_install: false # Set to false for production
          nginx_server_name: wiki.example.com
          letsencrypt_activate: true
          letsencrypt_https: true
          letsencrypt_domain: tls.example.com
          tags: [dokuwiki]

License
-------

MIT

Author Information
------------------

Romain Porte
