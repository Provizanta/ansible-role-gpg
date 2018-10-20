GPG generate
=========

Generate GPG keys.

Requirements
------------

None

Role Variables
--------------

keys: list of key parameters to be used for generating
  - user: user name
    email: e-mail associated with this key
    type: type of the key (e.g. RSA)
    length: length of the key
    passphrase: passphrase used to unlock the key
    expiration: when should the key expire (e.g. 0 for never)
    sub_keys:
      - purpose: type of the subkey (e.g. sign/encrypt)
        length: length of the subkey
        expiration: when should the subkey expire (e.g. 0 for never)
 

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
              - user: test
                email: test@test.com
                passphrase: test
                comment: "No comment is not the best comment."
                sub_keys:
                  - purpose: 'sign'
                    length: 2048
                  - purpose: 'sign,encrypt'
                    expiration: 1w

License
-------

MIT

Author Information
------------------

Tibor Csoka
