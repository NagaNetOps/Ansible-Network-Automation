# Ansible Configuration File Detection Test

## Objective

Verify which `ansible.cfg` file Ansible is using during playbook execution.

## Test Playbook

```yaml
---
- hosts: localhost
  gather_facts: false

  tasks:
    - name: Show config file
      ansible.builtin.debug:
        var: ansible_config_file
```

## Command Used

```bash
ansible-playbook check_ansible_config.yml
```

## Result

Output:

```text
TASK [Show config file] *************************************************
ok: [localhost] => {
    "ansible_config_file": "/home/ganapathi/Documents/Ansible-Network-Automation/Day-1/ansible.cfg"
}
```

## Conclusion

Ansible successfully detected and used the following configuration file:

```text
/home/ganapathi/Documents/Ansible-Network-Automation/Day-1/ansible.cfg
```

This confirms that the local `ansible.cfg` present in the project directory takes precedence and is being used during playbook execution.

## Verification Command

To verify the active configuration file directly from the command line:

```bash
ansible --version
```

Example output:

```text
config file = /home/ganapathi/Documents/Ansible-Network-Automation/Day-1/ansible.cfg
```

## Notes

* `ansible_config_file` is a built-in Ansible variable that displays the active configuration file path.
* `inventory_file` is only available when Ansible successfully loads a host from an inventory file.
* When running with the implicit localhost inventory, `inventory_file` may be undefined.

