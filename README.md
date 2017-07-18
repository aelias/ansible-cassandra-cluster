# Cassandra Cluster deployment
This example is about deploying a cassandra cluster with 3 nodes, in AWS using ansible.

## Prerequisites
- This solution assume the existense of 3 ubuntu-server (vanilla) based machines, correctly configured in AWS.
- Have ansible correctly installed in the host machine
- It assumes the host machine is a Fedora based machine (dnf package manager)
- The existense of a folder named ~/amazon/key-pairs, containing the pem file that is needed to access the machines remotly.
- The knowdlege of the private IPs of the machines.

## Configuration
- First at all, you have to configure the hosts file, located in the root folder of the solution. In this file, you have to configure de **public IPs** for each cassandra host (see the aliases cassandra1, cassandra2 and cassandra3)
- Configure the IPs for the seed nodes ./roles/cassandra/vars/main.yml (please see the var called: cassandra_seeds)
- Configure the IPs for the NO seed machines ./roles/cassandra/vars/main.yml (please see the var called: cassandra_no_seeds)

## Run the playbook
Just execute: *ansible-playbook site.yml --ask-vault-pass*, and wait for the results.

## Notes:
- The vault password is for my machine, so, in order to make it work in other machine, you have to create a new vault file (inside group_vars/control), with your own password, and inside it, a variable called: *control_sudo_pass* that contains your sudo password.

##Links for reference
- https://www.digitalocean.com/community/tutorials/how-to-run-a-multi-node-cluster-database-with-cassandra-on-ubuntu-14-04
- http://docs.datastax.com/en/cassandra/3.0/cassandra/initialize/initSingleDS.html
- http://docs.ansible.com
- 
Enjoy!
