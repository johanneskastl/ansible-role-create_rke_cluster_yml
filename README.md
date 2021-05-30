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

    - hosts: servers
      roles:
        - { role: 'johanneskastl.create_rke_cluster_yml' }

License
-------

BSD-3-Clause

Author Information
------------------

I am Johannes Kastl, reachable via kastl@b1-systems.de.
