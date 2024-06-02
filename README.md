
# Ansible role to install quay 3.10

Before running the Ansible role ensure that You have a Red Hat account and access to Red Hat repos.
We are using the podman to run the container, podman is provided by RHEL 9 Appstream repo - `rhel-9-for-x86_64-appstream-rpms`

This role configures the quay server with name - `quay-all.example.com`

1. Make sure you have ansible installed and you have SSH access to the host where you are going to install the quay.


```bash
# ansible --version
# ssh user@hostname
```

2. Clone repository


```bash
# git clone https://github.com/kaybee-singh/ansible-role-quay

```

4. Run the role 

```bash
# ansible-playbook role-playbook.yml
```
After successfull execution of role quayserver will be accessible at `http://quay-all.example.com`. Make sure you have make in entry in `/etc/hosts` for `quay-all.example.com`

## Authors

- [@kaybee-singh](https://www.github.com/kaybee-singh)
