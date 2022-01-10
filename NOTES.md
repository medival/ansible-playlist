### Preprequisite

### Instal dependencies

pip install ansible openstacksdk

### Install collection from ansible galaxy

ansible-galaxy collection install openstack.cloud

### Location clouds.yaml
~/.config/openstack/clouds.yaml

---

- name: Using Openstack Cloud collection
  hosts: localhost
  tasks:
  - openstack.cloud.server:
    name: vm
    state: present
    cloud: openstack
    region_name: ams01
    image: Ubuntu Server 14.04
    flavor_ram: 4096
    boot_from_volume: True
    volume_size: 75

---

- name: Using Openstack Cloud collection
  hosts: localhost
  collections:
  - openstack.cloud
    tasks:
  - server_volume:
    state: present
    cloud: openstack
    server: Mysql-server
    volume: mysql-data
    device: /dev/vdb
