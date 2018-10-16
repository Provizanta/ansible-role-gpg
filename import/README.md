GPG import
=========

Import GPG keys.

Requirements
------------

None

Role Variables
--------------

keys: list of parameters needed to identify the keys to be exported
  public: path to public key
  private: path to private key
  passphrase: passphrase that unlocks the key
  trust_file: path to trust

Dependencies
------------

None

Example Playbook
----------------
Specify the key parameters needed for key import.

    - hosts: localhost
      roles:
        - gpg/generate
          vars:
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
