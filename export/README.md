GPG export
=========

Export GPG keys.

Requirements
------------

None

Role Variables
--------------

keys: list of parameters needed to identify the keys to be exported
  email: e-mail associated with this key
  passphrase: passphrase used to unlock the key
  export_dir: directory, where public and private key along with revokation certificate are exported to

Dependencies
------------

None

Example Playbook
----------------
Specify the key parameters needed for key generation to be passed to the role.

    - hosts: localhost
      roles:
        - gpg/generate
          vars:
            keys:
              - email: test@test.com
                passphrase: test

License
-------

MIT

Author Information
------------------

Tibor Csoka
