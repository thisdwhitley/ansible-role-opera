# Ansible Role: opera

This is an Ansible role to install the [Opera](https://www.opera.com/) browser.

## Important Notes

* Initially I was configuring the repository for each OS and then installing the
  package via repo.  But the package install *also* created a repo, so I have
  opted to just install the latest version of the package, which installs a repo
  to keep it up to date
* I am using the `yum` and `apt` modules to allow for remote package install

## Requirements

Any package or additional repository requirements will be addressed in the role.

## Role Variables

There are no variables for this role.  It simply does the install and all of the
configuration is saved external to the app.

## Example Playbook

Playbook with various options specified:

```yaml
- hosts: localhost
  connection: local
  roles:
    - role: ansible-role-opera
```

## Inclusion

I envision this role being included in a larger project through the use of a
`requirements.yml` file.  So here is an example of what you would need in your
file:

```yaml
# get the opera role from github
- src: https://github.com/thisdwhitley/ansible-role-opera.git
  scm: git
  name: opera
```

Have the above in a `requirements.yml` file for your project would then allow
you to "install" it (prior to use in some sort of setup script?) with:

```bash
ansible-galaxy install -p ./roles -r requirements.yml
```

## Testing

I am relying heavily on the work by Jeff Geerling in using molecule for testing
this role.  I have, however, modified the tests to make them specific to what I
am attempting to accomplish but this could still use some work.

Please review those files, but here is a list of OSes currently being tested 
(using geerlingguy's container images):

* centos7
* fedora27
* fedora28
* fedora29
* ubuntu14
* ubuntu16
* ubuntu18
* debian8
* debian9

## To-do

* N/A

## References

* [How I test Ansible configuration on 7 different OSes with Docker](https://www.jeffgeerling.com/blog/2018/how-i-test-ansible-configuration-on-7-different-oses-docker)

## License

All parts of this project are made available under the terms of the [MIT
License](LICENSE).
