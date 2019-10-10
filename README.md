Ansible role: GPG
=========

[![Build Status](https://travis-ci.com/Provizanta/ansible-role-gpg.svg?branch=master)](https://travis-ci.com/Provizanta/ansible-role-gpg)

Manage GPG keys and trusts.

Requirements
------------

None

Role Variables
--------------

These variables are set in [defaults/main.yml](./defaults/main.yml):

    gpg_hide_secrets: true      # omit key details from logs

Other variables that can be set:

    gpg_generate:
      keys: <list, key parameters to be used for generating>
        - user: <string>
          email: <string, e-mail associated with this key>
          type: <string, key type (e.g. RSA)>
          length: <int>
          passphrase: <string, passphrase used to unlock the key>
          expiration: <date, when should the key expire (e.g. 0 for never)>
          sub_keys:
            - purpose: <string, subkey type (e.g. sign/encrypt)>
              length: <int, subkey length>
              expiration: <date, when should the subkey expire (e.g. 0 for never)>

    gpg_import:
      trusts: <list, trusts to import>
        - path: <string, path to trust>
      keys: <list, keys to import>
        - public: <string, path to public key>
          private: <string, path to private key>
          passphrase: <string, path to passphrase>

    gpg_export:
      dir: <string, destination for local trust file export>

      keys: <list, args for key exports>
        - email: <string>
          passphrase: <string, passphrase used to unlock the key>

      export_trust: <bool, should the trust be exported>
      harden: <bool, harden by removing the private master, leaving behind only subkeys>


Dependencies
------------

None

Example Playbook
----------------

Specify the parameters needed for GPG key manipulation.

    - hosts: localhost
      roles:
        - role: gpg
          vars:
            hide_secrets: yes
            gpg_generate:
              keys:
                - user: test
                  email: test@test.com
                  passphrase: test
                  comment: "No comment is not the best comment."
                  sub_keys:
                    - purpose: 'sign'
                      length: 2048

            gpg_export:
              dir: ~/test-gpg_export
              gpg_export_trust: yes
              harden: yes
              keys:
                - email: test@test.com
                  passphrase: test

            gpg_import:
              trusts:
                - path: "/path/to/trust.pgp"
              keys:
                - public: ~/public.key
                  private: ~/private.key
                  passphrase: test


License
-------

MIT

Author Information
------------------

Tibor Csóka
