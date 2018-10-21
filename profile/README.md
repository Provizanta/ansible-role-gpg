GPG profile
=========

Create a GPG profile using roles: gpg/generate, gpg/export and gpg/import.

Requirements
------------

None

Role Variables
--------------

gpg:
  generate: contains parameteres passed to gpg/generate
    ...
  export: contains parameters passed to gpg/export
    ...
  import: contains parameters passed to gpg/import
    ...

harden: specifies whether the generated profile should be hardened by removing the private master key

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
            gpg:
              generate:
                keys:
                  - user: test
                    email: test@test.com
                    passphrase: test
                    comment: "No comment is not the best comment."
                    sub_keys:
                      - purpose: 'sign'
                        length: 2048
              export: ...
              import: ...
            harden: yes

License
-------

MIT

Author Information
------------------

Tibor Csoka
