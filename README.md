create_rke_cluster_yml
=========

Create a cluster.yml for RKE based on the Ansible inventory

Requirements
------------

None.

Role Variables
--------------

- `rke_controlplane_nodes_group`: (required) the name of the Ansible group containing the controlplane nodes
- `rke_worker_nodes_group`: (optional) the name of the Ansible group containing the worker nodes
- `ssh_key_path`: (optional) filename or path to a private SSH key
- `path_to_cluster_yml`: (optional) path to the to-be-created cluster.yml, defaults to just `cluster.yml`

Dependencies
------------

None

Example Playbook
----------------

You can either run this role just targetting `localhost`:
```
- name: 'Prepare the cluster.yml on the Ansible control host'
  hosts: 'localhost'
  gather_facts: 'yes'
  become: 'false'

  roles:
    - role: 'create_rke_cluster_yml'
      vars:
        path_to_cluster_yml: '../cluster.yml'
        ssh_key_path: 'ssh_key_rke'
        rke_controlplane_nodes_group: 'rkeservers'
        rke_worker_nodes_group: 'rkeworkers'
```
Or you can run targetting all nodes, but only run the role once on localhost:

```
- name: 'Prepare the cluster.yml on the Ansible control host'
  hosts: 'all'
  gather_facts: 'yes'
  become: 'false'

  roles:
    - role: 'create_rke_cluster_yml'
      vars:
        path_to_cluster_yml: '../cluster.yml'
        ssh_key_path: 'ssh_key_rke'
        rke_controlplane_nodes_group: 'rkeservers'
        rke_worker_nodes_group: 'rkeworkers'
      delegate_to: 'localhost'
      run_once: 'true'
```

License
-------

BSD-3-Clause

Author Information
------------------

I am Johannes Kastl, reachable via kastl@b1-systems.de.
