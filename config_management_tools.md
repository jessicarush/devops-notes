# Configuration Management

## Table of Contents

<!-- toc -->

- [Introduction](#introduction)
- [Background](#background)
- [Comparison](#comparison)
  * [Ease of use](#ease-of-use)
  * [Management and Scheduling](#management-and-scheduling)
  * [Availability](#availability)
  * [Scalability](#scalability)
  * [Modules](#modules)
  * [GUI](#gui)
  * [Support](#support)
- [Summary](#summary)

<!-- tocstop -->

## Introduction

Configuration management (CM) tools, such as *Ansible* and *Puppet*, allow an admin to execute tasks on several servers at the same time as well as deploy multiple apps with just one click.

This text comes from [Ansible vs Puppet by Shivam Arora](https://www.simplilearn.com/ansible-vs-puppet-the-key-differences-to-know-article)

## Background

*Puppet* has been around since 2005 and is considered the biggest player in the CM market. It is produced by Oregon software development company Puppet. It was developed in Ruby, is open source and runs on all the major operating systems: Linux, Unix, Mac OS, and Windows. Oracle and Google run their data servers using Puppet. A commercial version, Puppet Enterprise, is available through PuppetLabs as well, and it includes professional support, but some users complain that PuppetLabs is too aggressive in pushing companies to buy it. Some users also say that Puppet is slow to adopt requested changes, such as adding new features and fixing bugs.

*Ansible* was introduced in 2012 by AnsibleWorks, is now owned by Red Hat, and has a much smaller market share than Puppet, which seems only natural since Puppet has been around longer. Like Puppet, it is open source and also has an enterprise version (Ansible Tower). But unlike Puppet, it was designed In Python (not Ruby) and is meant to be lightweight and have fast deployment. Since Python is built into most Unix and Linux systems, getting Ansible up and running can be done fairly quickly, and its agentless nature adds to the ease of setup and use. Also, the CLI accepts commands in almost any language, which is a big benefit. Ansible includes hundreds of modules to support a wide range of integrations, including Amazon Web Services (AWS). Ansible only recently began supporting Windows.


## Comparison

### Ease of use

Ansible is widely considered to be simpler to install and use. Puppet is model-driven and was built with systems administrators in mind. It follows a client-server (or agent-master) architecture; you install Puppet Server on one or more servers and then install Puppet Agent on all the nodes you want to manage. Puppet uses its own declarative language (also called domain-specific language, or DSL). The company says installation takes 10 to 30 minutes, depending on the environment and needs.

Ansible has a master but no agents running on the client machines—all functions are performed over SSH protocol. Being agentless is one of the features most touted in discussions about Ansible’s simplicity. And Ansible uses YAML syntax. Complex tasks are handled in configuration files called playbooks, and commands can be written in almost any programming language. Plus, Ansible is written in Python, which is built into most Unix and Linux deployments, making setup even easier/faster.

Despite being more complicated in some ways, Puppet does have advantages over Ansible in its use. A big one is that if you have syntax errors, they can be easily highlighted in Puppet before you run the task. In Ansible, tasks are executed in order and you won’t know if a specific task will fail until that task is executed. And YAML isn’t a particularly easy language to debug.

### Management and Scheduling

Management of Ansible vs. Puppet focuses on push and pull configurations. In Puppet, the client pulls configurations from the server, whereas in Ansible, the server pushes configurations to the nodes, for instantaneous deployment.

As for scheduling, in the default settings, Puppet Agent checks every 30 minutes to make sure the nodes are in the desired state. The free version of Ansible doesn’t include that capability; you’d need to use the enterprise version, Ansible Tower, for that.

### Availability

Both Ansible and Puppet have backups in case of failure, meaning availability need never be interrupted. Ansible has a secondary node in case the active node fails, and Puppet has more than one master in case the original master fails.

### Scalability

Both tools are highly scalable, meaning they can handle a big increase in nodes with no problem. However, scalability is generally considered to be easier in Ansible.

### Modules

Puppet Forge is Puppet’s repository/library; Ansible is called Ansible Galaxy. Forge is huge (almost 6,000 modules), and the modules can be marked as approved/supported by Puppet, so you won’t have to waste your time on ones that haven’t been proven to work. Galaxy doesn’t have this feature, so you may have to spend some time and effort changing things manually.

### GUI

Puppet’s graphical user interface (GUI) is more highly developed than Ansible’s. It’s used for viewing, managing and monitoring; for more complex tasks, you’ll probably use the command-line interface CLI, which is based on Ruby.

When it was introduced, Ansible was a command-line-only tool. Now you can get a UI if you use the enterprise version, but it’s by no means perfect. In fact, the GUI is sometimes not in sync with the command line, and it can’t do all the same things as the CL.

### Support

As Puppet has been around several years longer than Ansible, you can probably already guess that there would be more support for it and a bigger developer community—and you’d be right. There’s a dedicated support portal with a knowledge base, and two levels of professional support are offered: Standard (included) and Premium. You can also access a technical account manager (TAM) or become involved in the Puppet community (thousands of people) by attending events or participating in other channels. Puppet also offers a “State of DevOps” report annually that is a great resource for learning about DevOps trends.

Ansible offers two levels of professional support for its enterprise version. There are also more than 200 meetups around the world; a bigger gathering of users and contributors annually, called AnsibleFest; and mailing lists by topic, such as general questions, developer questions, and announcements. Overall, it has a smaller developer and user community than Puppet and the support and troubleshooting resources on the web.

## Summary

Many use Ansible for small, fast and/or temporary deployments, whereas Puppet is often used for more complex or longer-term deployments. If you have a mostly fixed set of machines to maintain, Puppet might be the better option, whereas if your machines are often being reprovisioned, Ansible might be the way to go.
