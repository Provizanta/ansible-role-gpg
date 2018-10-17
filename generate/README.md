GPG generate
=========

Generate GPG keys.

Requirements
------------

None

Role Variables
--------------

keys: list of key parameters to be used for generating

key.type: type of the key (e.g. RSA)
key.length: length of the key
key.sub_key.type: type of the subkey (e.g. RSA)
key.sub_key.length: length of the subkey
key.user: user name
key.email: e-mail associated with this key
key.passphrase: passphrase used to unlock the key
key.expire_date: when should the key expire (e.g. 0 for never)
key.export_dir: directory, where public and private key along with revokation certificate are exported to

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

License
-------

MIT

Author Information
------------------

Tibor Csoka
