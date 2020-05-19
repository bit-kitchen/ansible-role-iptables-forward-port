ansible-role-iptables-port-forward
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

```yml
- name: Forward traffic to port 443 to another host
  hosts: localhost
  gather_facts: yes
  roles:
  - name: bit_kitchen.iptables_port_forward
    self_addr: "{{ ansible_facts.eth0.ipv4.address }}"
    self_port: 80
    dest_addr: 10.20.30.40
    dest_port: 80
    protocol: tcp
  - name: bit_kitchen.iptables_port_forward
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
