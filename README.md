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

Infrastructure as Code (IaC):
This is the process of managing and provisioning IT infrastructure through machine‑readable, and I submit human‑readable definition files. And the idea is **instead of manual processes that you do over and over and over again**, like installing and configuring the NGINX web server on some Ubuntu hosts, **we use code files that are in say, a YAML format that declaratively describe the desired configuration of those manage nodes**. 
And the benefit there is that once your playbook is in place and it's working, you can run that over and over and over again and never worry about something like human error, human memory failures and that kind of thing.

How to check if ansible is installed? ansible --version

ansible-config -> this is just going to dump all of the current settings in your config file. And notice that it's just giving us a simple list of key value pairs.
there is e.g DEFAULT_HOST_LIST which shows config which ansible is using

ansible web -m ping -v - way to check connectivity to those remote hosts
