# Rekor Ansible

A playbook and associated roles to deploy sigstore's rekor on a Fedora
machine, with all the needed dependencies.

Once complete, you'll be able to test the rekor client and sign and verify
artifacts.

Currently, this installs:
- MariaDB
- Redis
- [Tillian](https://github.com/google/trillian)
- [rekor](https://github.com/sigstore/rekor)

If you have any of these already installed, you may want to comment out the
associated `include_role:` in the playbook.

**Warning**: currently, the `trillian` role will use a
[script](/roles/trillian-log-server/files/createdb.sh) to prepare the
MySQL-compatible database which will drop and recreate a database called "test".
So make sure you don't have a database of that name that you care about on the
target machine before running the playbook.

## How to use

Ensure you have Ansible installed on the host from which you want to run the
playbook. Then:  
`ansible-playbook -k -i path/to/your/inventory.yml playbook.yml`

## Try out rekor

This playbook will automatically start MariaDB and Redis, but purposely doesn't
start any of the other servers that are more specific to rekor. This means you
will have to start the trillian log server, trillian log signer and rekor server
yourself before you can use `rekor`, the rekor cli tool.

You will need to start these all individually, following the instructions on the
[sigstore website](https://sigstore.dev/get_started/server/)  may want to
install tmux on the target machine to do so (`dnf install -y tmux`).

You can then follow the [instructions](https://sigstore.dev/get_started/client/)
on using the rekor cli tool.

# Contribute

Contributions are welcome!

This playabook and any of its roles currently only support Fedora (tested on
Fedora 33). They may support RHEL and CentOS, but is currently untested.
Any help in testing and supporting more environments is welcome.

# Contributers and credits

- axel simon (axel@redhat.com)

Based in large part on [keylime-vagrant-ansible-tpm-emulator](https://github.com/keylime/keylime-vagrant-ansible-tpm-emulator/).
