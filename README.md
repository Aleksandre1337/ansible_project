# Ansible Project

This project automates the setup of a client host using Ansible. It includes playbooks and roles organized in a structured hierarchy.

## Project Structure

```
.
├── ansible.cfg
├── inventory
└── roles
    └── client-setup
        ├── README.md
        ├── defaults
        │   └── main.yml
        ├── files
        │   ├── bar-file1
        │   ├── bar-file2
        │   ├── baz-file1
        │   ├── baz-file2
        │   ├── foo-file1
        │   └── foo-file2
        ├── handlers
        │   └── main.yml
        ├── meta
        │   └── main.yml
        ├── tasks
        │   └── main.yml
        ├── templates
        │   └── client.j2
        ├── tests
        │   ├── inventory
        │   └── test.yml
        └── vars
            └── main.yml
```

### Description:

- `ansible.cfg`: Ansible configuration file.
- `inventory`: File listing the hosts to be managed by Ansible.
- `roles`: Directory containing all roles used in the project.
- `client-setup`: Role for setting up the client host.
- `README.md`: Detailed information about the role.
- `defaults`: Directory containing default variable values.
- `main.yml`: Default variable values for the role.
- `files`: Directory containing files to be copied to the client host.
- `handlers`: Directory containing handlers for the role.
- `main.yml`: Handler tasks.
- `meta`: Directory containing metadata for the role.
- `main.yml`: Metadata for the role.
- `tasks`: Directory containing tasks for the role.
- `main.yml`: Main tasks file.
- `templates`: Directory containing templates for the role.
- `client.j2`: Jinja2 template for the Message of the Day (MOTD).
- `tests`: Directory containing test files for the role.
- `vars`: Directory containing variables for the role.
- `main.yml`: Variable definitions for the role.

## Usage

Run the main playbook with the following command:

```bash
ansible-playbook playbooks/setup_client.yml
```

## Role Details

The `client-setup` role performs the following tasks:

- Configures various settings on the client host including timezone, hostname, and software installations.
- Sets up the Message of the Day (MOTD) to display system information.
- Creates directories and copies corresponding files to the client host.

More detailed information :

## Tasks

The playbook performs the following tasks:
`
    1. Logs into the client host via SSH using an SSH key/Pem Key.

    2. Changes the timezone to Europe/Spain.

    3. Changes the hostname.

    4. Installs the following tools with a single task:
        - vim
        - telnet
        - htop
        - iotop
        - atop
        - mc
        - traceroute
        - unzip

    5. Configures the Message of the Day (MOTD) to display the following information when logging in via SSH:
        - The IP address of the machine
        - The username
        - The hostname
        - The installed OS
        - The time
        - The timezone
        - MOTD Warning Message

        Note: This information is dynamic and will update based on the machine you're logging into.

    6. Creates the following directories in the `/opt` directory:
        - academy-foo
        - academy-bar
        - academy-baz

    7. Copies the corresponding files into these directories. The files are named as follows:
        - foo-file1
        - foo-file2
        - bar-file1
        - bar-file2
        - baz-file1
        - baz-file2