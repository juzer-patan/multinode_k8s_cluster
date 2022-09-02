System Requirements
------------
- Ansible Version ```2.9.+```

Getting Started
------------
This repository contains Ansible Roles which will 
- Launch ec2-instances 
- Configure one of these instances as the Kubernetes Master Node 
- Join them Worker Nodes to the master.All of this will be automated

Steps
------------
- Clone the GitHub repo
```
git clone https://github.com/juzer-patan/multinode_k8s_cluster.git
```
- Replace your AWS Key with the file ```aws_key.pem```
- Make the key executable using 
```
chmod 400 key_name.pem
```
- Update the Key name in the ```ansible.cfg``` file
```
private_key_file= "Your_Key_Name".pem
```
- Update the variables in the roles ```aws_master/vars/main.yml``` and ```aws_slave/vars/main.yml``` files 
```
master_tag_name : "Tags which you want to assign to your instance"
security_id : "The security group id to be attached to your instance"
key_name : "The private key name for ssh authentication"
subnet_name : "The subnet in which the instance will be launched"
ami_id : "The ami id from which the instance will be launched"
instance_type : "The type of instance and the resources which you want for your instance"
region_name : "The region in which the instance will be launched"
count : "Number of Worker Nodes to be launched" 

```

- Launch the ec2-instances from the playbook ```ec2_instances.yml```
```
ansible-playbook ec2_instances.yml
```
- Configure the Multi-Node Cluster by just running one single playbbok ```multinode_cluster.yml```
```
ansible-playbook multinode_cluster.yml
```
With just one click,the cluster will be successfully launched

Cluster Verification
------------
Once the cluster is launched,we can connect to the master node and verify the cluster readiness using
```
kubectl get nodes
```
Connect With Me
------------
- [LinkedIn](https://www.linkedin.com/in/juzer-patanwala-7b1963173)
