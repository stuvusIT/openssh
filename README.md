# openssh

This role sets up and configures an OpenSSH server along with the system-wide SSH client configuration.
A new moduli file consisting only of 4096 and 8192 bit moduli is created asynchronously.

## Requirements

Ubuntu or Arch Linux

## Role Variables

| Name          | Default/Required | Description                                                      |
|---------------|:----------------:|------------------------------------------------------------------|
| `ssh_config`  | `{}`             | Dict with all host matches consisting of dicts of ssh options    |
| `sshd_config` | See below        | Dict with the sshd configuration. See below for more information |

### sshd configuration

| Name           | Default/Required | Description                                                |
|----------------|:----------------:|------------------------------------------------------------|
| `config`       | `{}`             | Dict with all configuration options for the OpenSSH daemon |
| `userMatches`  | `{}`             | Dict with all user matches for the OpenSSH daemon          |
| `groupMatches` | `{}`             | Dict with all group matches for the OpenSSH daemon         |
| `hostMatches`  | `{}`             | Dict with all host matches for the OpenSSH daemon          |

## Example Playbook

```yml
- hosts: all
    roles:
      - openssh
        ssh_config:
          "*":
            Protocol: 2
        sshd_config:
          config:
            PermitRootLogin: "no"
          userMatches:
            alice:
              AcceptEnv: "*"
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).


## Author Information

- [Janne Heß](https://github.com/dasJ)
