# Deploying MinIO on Baremetal/VM using Ansible

This playbook deploys MinIO on baremetal/vm using Ansible.

THIS PLAYBOOK IS NOT PRODUCTION READY. USE AT YOUR OWN RISK.

## Features

- Deploys MinIO on baremetal
- Discovers unmounted disks and formats them as XFS, labels the disks, mounts them and adds them to `/etc/fstab`
- Creates a MinIO user and group and sets the ownership of the data directory to the MinIO user
- Installs MinIO server based on the specified version in the `group_vars/all.yml` file and installs the MinIO client
- Configures MinIO as a systemd service
- Updates the `/etc/default/minio` file with the required environment variables
- Loads TLS certificates and keys from a directory into the `$MINIO-USER/.minio/certs` directory
- Starts the MinIO service

## Prerequisites

- Ansible 2.9 or later
- Ubuntu 22.04 or later
- RHEL Based systems 8.0 or later

## Usage

1. Clone this repository `git clone`
2. Copy `inventory/inventory.dist` to `inventory/inventory` and update the inventory file with the IP addresses of the hosts.
3. Copy `group_vars/all.yml.dist` to `group_vars/all.yml` and update the variables as per your requirements.
4. (Optional if TLS is enabled) Add your TLS certificates and keys to the `/roles/minio/files/certs` directory. They should be called `public.crt` and `private.key` respectively. Also, if you are using a CA self-signed certificate, add the CA certificate to the same directory and name it `ca.crt`.
4. Run the playbook `ansible-playbook -i inventory/inventory main.yml`

## Advanced Usage

You can also call specific plays based on the tags. For example, if you want to only format the disks, you can run `ansible-playbook -i inventory/inventory main.yml --tags format_disks`.