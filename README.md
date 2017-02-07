# Kibana

Master: [![Build Status](https://travis-ci.org/sansible/kibana.svg?branch=master)](https://travis-ci.org/sansible/kibana)  
Develop: [![Build Status](https://travis-ci.org/sansible/kibana.svg?branch=develop)](https://travis-ci.org/sansible/kibana)

* [ansible.cfg](#ansible-cfg)
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

This role installs Kibana.

For more information on Kibana please visit [elastic kibana](https://www.elastic.co/products/kibana).

**Note** Supports Kibana 4




## ansible.cfg

This role is designed to work with merge "hash_behaviour". Make sure your
ansible.cfg contains these settings

```INI
[defaults]
hash_behaviour = merge
```




## Installation and Dependencies

To install run `ansible-galaxy install sansible.kibana` or add this to your
`roles.yml`

```YAML
- name: sansible.kibana
  version: v1.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`


Pre download the kibana.tar.gz from elastic site. 
```
ansible-playbook roles/gikoluo.kibana/prefetch.yml -i vagrant -v
```


## Tags

This role uses two tags: **build** and **configure**

* `build` - Installs Kibana and all it's dependencies.
* `configure` - Configure and ensures that the Kibana service is running.




## Examples

To install the defaul version (4.1.2):

```YAML
- name: Kibana
  hosts: "{{ hosts }}"

  roles:
    - role: kibana
```

To install RC 5

```YAML
- name: Kibana
  hosts: "{{ hosts }}"

  roles:
    - role: kibana
      kibana:
        tarball: "kibana-5.0.0-rc1-linux-x86_64"
        download_base_url: https://artifacts.elastic.co/downloads/kibana/
        version: 5.0.0-rc1
```

To install a specific version:

```YAML
- name: Kibana
  hosts: "{{ hosts }}"

  roles:
    - role: kibana
      kibana:
        tarball: kibana-4.5.2-linux-x64
        version: 4.5.2
```
