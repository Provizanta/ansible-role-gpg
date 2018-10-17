GPG export
=========

Export GPG keys.

Requirements
------------

None

Role Variables
--------------

trust:
  export_dir: destination for local trust file export

keys: list of parameters needed to identify the keys to be exported
  email: e-mail associated with this key
  passphrase: passphrase used to unlock the key
  export_dir: destination for public and private key exports

Dependencies
------------

None

Example Playbook
----------------
Specify the key parameters needed for key generation to be passed to the role.

    - hosts: localhost
      roles:
        - gpg/export
          vars:
            trust:
              export_dir: ~/test-export
            keys:
              - email: test@test.com
                passphrase: test
                export_dir: ~/test-export/test-account-backup

License
-------

MIT

Author Information
------------------

Tibor Csoka
