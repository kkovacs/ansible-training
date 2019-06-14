
# Intro

- Ender's game
- Agent-less, works via SSH
- Only needs python on the other side

# Lesson 1: Basic shell command

Make hosts file:

	test1 ansible_host=x.x.x.x ansible_user=vagrant ansible_port=22 ansible_ssh_private_key_file=...
	test2 ansible_host=... ansible_user=... ansible_port=... ansible_ssh_private_key_file=...

Test with:

	ansible -i hosts all -m ping

	ansible -i hosts all -m setup

	ansible -i hosts all -m shell -a "cat /etc/os-release"

Mention:

- `-v`
- `-vvv`
- `--limit -l`

Further reading: https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html

# Lesson 2: Idempotency

Operations better not run always.

Mention:
- script command (copy+run)

# Lesson 3: apt

Further reading: https://docs.ansible.com/ansible/latest/modules/modules_by_category.html

# Lesson 4: copy

Mention:
- multiple tasks in one file
- `--diff` `-D`
- `--check` `-C`
- `force: no` (No overwrite)
- `src` instead of `content`
- `synchronize` module (= rsync)

https://docs.ansible.com/ansible/latest/modules/copy_module.html

# Lesson 5: copy with template

Mention:
- `sysctl` module
- `template` module ("for", "if", etc inside)
- grouping hosts
- host group variables
- command line `-e` envvars
- vault

# Lesson 6: lineinfile

Mention:
- `replace` module
- `blockinfile` module
- `assemble` module

# Lesson 7: lineinfile + with

Mention:
- `after`, `before`, `insertafter` options
- `ini` module

Further reading: https://docs.ansible.com/ansible/latest/user_guide/playbooks_loops.html

# Lesson 8: handlers

Mention:
- multiple handlers
- `register` / `when xxx is changed`

# Lesson 9: with + hostvars

Mention:
- `ansible -i hosts all -m setup`
- `when` on tasks

Further reading: https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html

# Finally, mention:

- Lots of modules: `authorized_key`, `cron`, `group`, `user`, `systemd`, `mount`, `firewalld`, `datadog`
- mysql/postgresql modules (db, user, replication)
- `git` module
- `fetch` module
- `telegram` module
- `nagios` module (schedule downtime for all hosts, etc) 
- `debug` module
- including playbooks
- automatic inventories
- provisioning!
- delegate_to to run locally or different server
- deploy strategies (for example, 1/2 + 1/2, or 1 + 1/3 + 1/3 + 1/3)
- `--start-at-task` option
- more complex playbook organization (roles-based)

# Exercise:

Put all of our SSH keys into the system.

https://docs.ansible.com/ansible/latest/modules/authorized_key_module.html

# Final demo

Turn all of them into honeypots with our honeypot script :)

