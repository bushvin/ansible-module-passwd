# ansible-module-passwd
An ansible module to allow regular users to change their password

## Autors
[William Leemans](https://github.com/bushvin)

## Requirements
python-expect or pexpect needs to be installed on the target system

## Installation
Copy the passwd module file to your module library. Information on where this is
can be typically found in /etc/ansible/ansible.cfg

Or you can include it in the library/modules directory in the base of your playbook.

## Usage
    - name: change my password
        username: <username>
        current_passwd: <the current password of the user>
        new_passwd: <the new password for the user>
        binary: </path/to/the/passwd/binary>
        timeout: <timout to wait for expect>

where:

- **username** *optional*, the name of the user to change the password for, by default this is you.
- **current_passwd** *optional*, the current password of the user
- **new_passwd** *optional*, the new password for the user
- **binary** *optional*, the full pth to the passwd binary, by default /usr/bin/passwd
- **timeout** *optional*, the timout for expect to wait for feedback from stdout, by default 30 seconds

## Examples
Examples can be found inside the module

## limitations
As a normal user is unable to displey their password hash, it is impossible to 
create n idempotent passwd module. Hence this module will be skipped during a check
run
