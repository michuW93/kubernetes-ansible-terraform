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

Variables in ansible: A variable in Ansible is the same as a variable in any other programming or scripting language, it's a placeholder
example with YAML syntax: 
``` install_path: /opt/myapp ```
referencing a variable:
``` - dest: '{{ install_path }}/foo.cfg'```

Ansible has a totally separate set of built‑in modules for Windows. So **user** is the Python script that's used with Linux environments, **win_user** is the one used with Windows, you see, because Ansible on Windows is totally different inasmuch as it doesn't use SSH for transport, it uses WinRM and WSMAN.

An Ansible role is a reusable standalone component that encapsulates a set of Ansible tasks and configurations. I would suggest that you think of roles as the rough equivalent of functions in a traditional programming language, so you're encapsulating logic.
we use ansible‑galaxy init to create and scaffold the new role in your target directory


An Ansible template is a file that contains configuration parameters, but it's dynamic. The dynamic values get plugged in from your Ansible playbooks or from your other artifacts, like inventory, variable file. Templates use the Jinja2 templating language.

# terraform

Base on **Ned Bellavance** tutorial

Infrastructure as Code is provisioning infrastructure through software to achieve consistent and predictable environments.
A few that I want to call out is the fact that this is all being done through code and software. It's not a manual process. And the goal here is to achieve consistency. That means every time you use code to deploy infrastructure, it does so in a consistent way and that the environment you get at the end is predictable.

Benefits of IaaC?
* One big benefit is the reusability of your code. Once you've figured out how to properly deploy, say, a database server for a particular application, you can take the code for that database server deployment and reuse it in any other application that needs a similar database server back end. Having those reusable components will make your life a lot easier
* Defining your Infrastructure as Code opens the door to automation. You're no longer clicking around in a portal or banging out commands at a terminal. You can take your Infrastructure as Code and integrate it with an automation process or pipeline with well‑defined inputs and outputs

Core concepts:
* It's defined in code,
* stored in source control e.g GitLab
* it's declarative or imperative,
* idempotent(Terraform attempts to be idempotent in the sense that if you haven't changed anything about your configuration and you apply it again to the same environment, nothing will change in the environment because your defined configuration matches the reality of the infrastructure that exists) and consistent (Each time you do something, the results should be the same).

Terraform is an example of a declarative approach to deploying insfrastructure as code.
Declarative means to tell what I want, not how to do it.
Example with pizza. In imperative way it would be:
```
get pizza dough
get cheese
get ham

put cheese on the pizza dough
put ham on the cheese
```

so here you must tell what to do and how to do.
In declarative way it would be:
```
food pizza "pizza" {
 ingrediens = [
  "pizza dough", "chesse", "ham"
 ]
}
```
here we declare what we want and we leave it to software to figure out exactly how to implement what I want.

State data - once resources have been created, Terraform likes to keep track of what's going on, so it maintains state data which contains the current information about your deployment. It's a mapping of what you've defined in your configuration to what exists in the target environment. When you want to do an update of your environment, Terraform essentially compares your updated config to what's in the state file, calculates the changes to make the state match config, and makes the changes in the target environment, finally updating the state data.

Installing Terraform is simple:
* download executable for your platform
* Add yo your PATH environment variable
Terraform is also available in common package managers like apt and Chocolatey
