# kubernetes

control plane nodes and worker nodes

containers must be inside pod. In pod there can be 1 or more containers but in general odd numbers are better in kubernetes.

Pod is shared execution env and shared execution env is basically collection of things app needs to run.

scaling in kubernetes is about adding removing pods, not about adding contatiners into pod

pod life cycle: PENDING, RUNNING, SUCCEEDED/FAILED

only healthy Pods will have traffic



# ansible

Base on Tim Warner tutorial

Configuration Management (CM) - CM is the process of systematically managing, organizing, and controlling changes in your information technology or IT system. CM helps in establishing and maintaining consistency of your system's performance as well as its attributes.
It's annoying when you check the system state of a server and find that it's deviated from where you need it to be, its desired state. CM platforms allow you to anchor that consistency and if a server does happen to drift out of its desired state, we can have the configuration management system bring it back.

Ansible Competitors: Puppet, Terraform
