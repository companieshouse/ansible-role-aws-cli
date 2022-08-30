# Ansible Role: AWS CLI

An [Ansible Galaxy](https://galaxy.ansible.com/) role for installing or updating [AWS Command Line Interface](https://aws.amazon.com/cli/).

## Role Variables

The role defaults (see `defaults/main.yml`) use Amazon's official installer URL for the 64-bit Linux package:

```
https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip
```

To specify a different location for the installer package, override the `aws_cli_url` role variable in your playbook:

```yaml
aws_cli_url: https://...
```

If AWS CLI is already installed at the default location of `/usr/local/bin/aws` this role will make no changes. To ensure that the latest available version of AWS CLI is always installed or an existing installation is updated (not idempotent) override the `aws_cli_update` role variable:

```yaml
aws_cli_update: true
```

This role creates a temporary directory under `/tmp` where the AWS CLI installer and associated files are extracted before the AWS CLI `install` script is executed. The temporary directory is removed after the script completes. If the `/tmp` directory on the target host(s) resides on a filesystem that is mounted with the `noexec` option, installation will fail with a 'Permission denied' error as the `install` script cannot be executed in this scenario. Specify an alternative path in this case, using the `temp_dir` role variable, to a directory without execution restrictions:

```
temp_dir: "/home/{{ ansible_user }}"
```

In this case a temporary directory will be created inside `/home/{{ ansible_user }}` and removed at the end of the role.

## Example Requirements File

```yml
- src: https://github.com/companieshouse/ansible-role-aws-cli
  name: aws-cli
  version: "n.n.n"
```

## Example Playbook

```yml
    - hosts: servers
      roles:
        - aws-cli
```

## License

MIT
