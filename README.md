A set of Ansible playbooks and roles to automatically configure a Fedora GNOME Workstation the way I like it...

# Pre-requisites

* Install Fedora from a vanilla Fedora GNOME Live ISO
* git clone https://github.com/rsriniva/fedora-setup.git
* cd fedora-setup
* sudo dnf install ansible python3-libdnf5 -y
* Download Red Hat VPN files and copy them to /tmp. Edit the roles/vpn/tasks/main.yaml file and replace the RPM files names in the "Install Red Hat specific VPN rpms" task.
* Copy your SSH private and public key files (named `id_rsa` and `id_rsa.pub` respectively) to /tmp for the "sshconfig" role.

# Playbook Run

* Read through and set appropriate values in the group_vars/all.yaml file (username, email, hostname etc)
* ansible-playbook setup.yaml -K --check (check if everything is OK)
* ansible-playbook setup.yaml -K (run the playbook when check returns no error)

# Run Selective Playbook Tasks
* Dump all tags using ansible-playbook setup.yaml --list-tags
* ansible-playbook setup.yaml -K -t tag1, tag2 for selective task runs
