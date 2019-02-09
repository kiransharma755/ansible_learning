---
[master-and-node:children]
master
nodes

[master]
bipratech2c.mylabserver.com ansible_connection=local ansible_host=13.59.45.139 ansible_user=cloud_user ansible_ssh_extra_args='-o StrictHostKeyChecking=no'

[nodes]
bipratech3c.mylabserver.com ansible_host=18.217.212.20 ansible_user=cloud_user
bipratech4c.mylabserver.com ansible_host=52.15.84.82 ansible_user=cloud_user

Notes

ansible_ssh_extra_args='-o StrictHostKeyChecking=no' supresses the message of 
bipratech3c.mylabserver.com | FAILED! => {
    "msg": "Using a SSH password instead of a key is not possible because Host Key checking is enabled and sshpass does not support this.  Please add this host's fingerprint to your known_hosts file to manage this host."
