Ansible-Role: RootKeys
========================

This role installs the ssh-keys for simultated administrators in the AECID 
Testbed.

Requirements
------------

No special requirements

Role Variables
--------------

```
# should the private key installed?
rootkeys_install_private: False
# should the public key installed?
rootkeys_install_public: True

# which user should be authorized by the public key?
rootkeys_public_key_user: root
# User that holds the private key
rootkeys_private_key_user: root
# Directory where the private key should be stored
rootkeys_private_dir: "/root/.ssh"

rootkeys_private: |
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACAULlkY9CE9bFp2PrAXUQyMY1Hr7ltbopEcEO8deTKfuQAAAJBxW1xRcVtc
UQAAAAtzc2gtZWQyNTUxOQAAACAULlkY9CE9bFp2PrAXUQyMY1Hr7ltbopEcEO8deTKfuQ
AAAECPOwKRVHK+txAr5AyhQJN9P8fJqHy8fDomx2jQtXaMoxQuWRj0IT1sWnY+sBdRDIxj
UevuW1uikRwQ7x15Mp+5AAAAB3Jvb3RrZXkBAgMEBQY=
-----END OPENSSH PRIVATE KEY-----


rootkeys_public: "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBQuWRj0IT1sWnY+sBdRDIxjUevuW1uikRwQ7x15Mp+5 rootkey"
```


Example Playbook
----------------

Install the public key for user aecid:
```
    - hosts: localhost
      roles:
         - role: rootkeys
           vars: 
             rootkeys_public_key_user: aecid
```


Install the private key for user root:
```
    - hosts: localhost
      roles:
         - role: rootkeys
           vars:
             rootkeys_install_private: True
             rootkeys_install_public: False
```

License
-------

GPL-3.0

Author Information
------------------

Wolfgang Hotwagner (https://www.ait.ac.at)
