
# Ansible role to install quay 3.10

Before running the Ansible role ensure that You have a Red Hat account and access to Red Hat repos.
We are using the podman to run the container, podman is provided by RHEL 9 Appstream repo - `rhel-9-for-x86_64-appstream-rpms`

This role configures the quay server with name - `quay-all.example.com`

1. Make sure you have ansible and git installed on the system where you want to install the quay. This configuration is created for running ansible locally, so role will create the quay registry on the same system where you are running the ansible commands.  


```bash
sudo -i
yum install ansible-core git
ansible --version
git --version
```

2. Install required ansibile collections and clone the git repository.


```bash
ansible-galaxy collection install ansible.posix
ansible-galaxy collection install community.general
ansible-galaxy collection install containers.podman
git clone https://github.com/kaybee-singh/ansible-role-quay /root/ansible-role-quay

```

4. Run the role 

```bash
cd /root/ansible-role-quay;ansible-playbook role-playbook.yml
```
5. After successfull execution of role quayserver will be accessible at `http://quay-all.example.com`. Make sure you have make in entry in `/etc/hosts` for `quay-all.example.com`

6. If you are not able to access the WebUI then try below
  - Make sure you have an entry in your /etc/hosts for quay-all.example.com
  - Verify that three containers are running
    ```bash
    podman ps
    ```
  - If quay container is not started, chech its logs, fix the issue and then start the container.
    ```bash
    podman logs quay
    podman start quay
    ```
 

## Authors

- [@kaybee-singh](https://www.github.com/kaybee-singh)
