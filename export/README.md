GPG export
=========

Export GPG keys.

Requirements
------------

None

Role Variables
--------------

export_dir: destination for local trust file export

keys: list of parameters needed to identify the keys to be exported
  id: key-id (e.g. e-mail associated with this key
  passphrase: passphrase used to unlock the key

export_trust: indicate whether the trust should be exported (mandatory)

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
            export_trust: True
            export_dir: ~/test-export
            keys:
              - id: test@test.com
                passphrase: test

License
-------

MIT

Author Information
------------------

Tibor Csoka
