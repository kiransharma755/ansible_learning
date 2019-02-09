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


When I run as this, get this error but if I run with hostpatter nodes or master or master-and-node, it works. 
( need to fix)

[root@bipratech1c cloud_user]# ansible all -m ping  -i hosts-file.ini --ask-pass
SSH password:
--- | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: unknown option -- -\r\nusage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]\n           [-D [bind_address:]port] [-E log_file] [-e escape_char]\n           [-F configfile] [-I pkcs11] [-i identity_file]\n           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]\n           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]\n           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]\n           [user@]hostname [command]\n",
    "unreachable": true
}
bipratech2c.mylabserver.com | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
bipratech3c.mylabserver.com | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
bipratech4c.mylabserver.com | SUCCESS => {
    "changed": false,
    "ping": "pong"
