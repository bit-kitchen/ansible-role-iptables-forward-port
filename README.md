ansible-role-iptables-forward-port
==================================

An ansible role that configures iptables for port forwarding.

Requirements
------------

None.

Role Variables
--------------

None.

Dependencies
------------

None.

Example Playbook
----------------

### Add forwarding rules

```yml
- name: Forward traffic to port 443 to another host
  hosts: localhost
  gather_facts: yes
  roles:
  - name: bit_kitchen.iptables_forward_port
    self_addr: "{{ ansible_facts.eth0.ipv4.address }}"
    self_port: 80
    dest_addr: 10.20.30.40
    dest_port: 80
    protocol: tcp
  - name: bit_kitchen.iptables_forward_port
    self_addr: "{{ ansible_facts.eth0.ipv4.address }}"
    self_port: 443
    dest_addr: 10.20.30.40
    dest_port: 443
    protocol: tcp
```

### Remove forwarding rules

```yml
- name: Disable forwarding traffic to port 443 to another host
  hosts: localhost
  gather_facts: yes
  roles:
  - name: bit_kitchen.iptables_forward_port
    remove: yes
    self_addr: "{{ ansible_facts.eth0.ipv4.address }}"
    self_port: 80
    dest_addr: 10.20.30.40
    dest_port: 80
    protocol: tcp
  - name: bit_kitchen.iptables_forward_port
    remove: yes
    self_addr: "{{ ansible_facts.eth0.ipv4.address }}"
    self_port: 443
    dest_addr: 10.20.30.40
    dest_port: 443
    protocol: tcp
```

License
-------

[MIT](LICENSE)

Author Information
------------------

[bit.kitchen](https://github.com/bit-kitchen)
