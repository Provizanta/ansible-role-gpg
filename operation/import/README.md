GPG import
=========

Import GPG keys.

Requirements
------------

None

Role Variables
--------------

trusts:
  - path: path to the trust to be imported

keys:
  - public: path to the public key
    private: path to the private key
    passphrase: passphrase for the key specified

Dependencies
------------

None

Example Playbook
----------------
Specify the key parameters needed for key import.

    - hosts: localhost
      roles:
        - gpg/operation/import
          vars:
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

Tibor Csoka
