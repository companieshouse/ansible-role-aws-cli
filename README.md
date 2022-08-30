# Ansible Role: AWS CLI

An [Ansible Galaxy](https://galaxy.ansible.com/) role for installing or updating the latest version of [AWS Command Line Interface](https://aws.amazon.com/cli/).

## Role Variables

The role defaults (see `defaults/main.yml`) assume Amazon's official installer URL for the 64-bit Linux package:

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
