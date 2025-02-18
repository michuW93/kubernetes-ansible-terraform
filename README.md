# kubernetes

control plane nodes and worker nodes

containers must be inside pod. In pod there can be 1 or more containers but in general odd numbers are better in kubernetes.

Pod is shared execution env and shared execution env is basically collection of things app needs to run.

scaling in kubernetes is about adding removing pods, not about adding contatiners into pod

pod life cycle: PENDING, RUNNING, SUCCEEDED/FAILED

only healthy Pods will have traffic



# ansible

Base on **Tim Warner** tutorial

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

Ansible is a Python application, so both your control node, as well as your managed nodes are going to need to have Python installed.

Two distributions:
* ansible-core - just the essentials: command-line tools and essential modules
* ansible: everything with collections of modules, plugins, and roles

you can set up a Windows Server or even a Windows client machine as an Ansible control node, the Ansible command‑line tools are Linux only, so you're going to have to set up Windows Subsystem for Linux, or WSL, on your Windows machine and then install Ansible in your WSL environment



The first thing Ansible will look at on your server is the presence of an environment variable in memory called ansible_config, and that would be a path to an ansible.cfg configuration file. If you don't have that environment variable set, the next place Ansible looks is in the current directory

a playbook is simply a text-based YAML file that defines a configuration. Playbook is a YAML task automation script. It's critically important that you think about Ansible and its Playbooks as being both declarative and idempotent
So, from now on the idea is once you have your nGINX web server installation and configuration Playbook all debugged and ready to rock, you can use it from now to perpetuity and not have to worry about human error forgetting stuff because if it's encapsulated in the Playbook, it will happen. And I hope that you're keeping your Playbooks, like all the rest of your Ansible source files, in version control

![image](https://github.com/user-attachments/assets/39cd37ba-9286-44f0-a508-c85f7c4db68c)

To create custom modules (units of code that control system resources of execute system commands on local and remote nodes e.g copy or lookup) or plugins(units of code that extend Ansible core functionality) you need to know Python.

Ansible Galaxy is a public/private repository. It's at galaxy.ansible.com

What we're talking about here is a business who has a number of Playbooks and you're finding that instead of deploying the Playbooks one by one by one, you want to bundle them together so that when you're setting up servers and managing servers, you can do everything from one spot. And there's two levels of abstraction. The highest level of abstraction is an artifact called a collection, and the collection consists of one or more roles

 Running ansible playbooks:
 * ansible-playbook cli command
 * CI/CD pipelines
 * scheduled cron jobs
 * automation controller/WX
 * ansible-pull command
 * container orchestrations (Kubernetes)

use Ansible Vault and an encrypted secrets.yml file to store passwords and API keys in playbooks securely
