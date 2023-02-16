Lab 13. Getting Started with Ansible
===================================


In this lab, we will begin to teach you the practical skills to
cover the very fundamentals of Ansible, starting with how to install
Ansible. We\'ll then look at node
requirements and how to validate your Ansible installation.


#### Lab Environment

Note that `root` user password is **fenago**

All lab file are present at below path. Run following command in the terminal first before running commands in the lab:

```
cd ~/Desktop/gitlab-ci-ansible-course
mkdir Lab_13
cd Lab_13
```

<span style="color:red;">Make sure that your lab environment's `/etc/hosts` file has all host entries present in `hosts.txt` file which is located at the root folder.</span>

#### Ansible version

You can run the `ansible --version` command, you will see output similar to the following: 

```
ansible --version
ansible 2.9.6
  config file = None
  configured module search path = ['/Users/james/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/Cellar/ansible/2.9.4_1/libexec/lib/python3.8/site-packages/ansible
  executable location = /usr/local/bin/ansible
  python version = 3.8.1 (default, Dec 27 2019, 18:05:45) [Clang 11.0.0 (clang-1100.0.33.16)]
```


Understanding how Ansible connects to hosts
-------------------------------------------


Let\'s focus on the INI formatted inventory. An example is
shown here with four servers, each split into two groups. Ansible
commands and playbooks can be run against an entire inventory (that is,
all four servers), one or more groups (for example, [webservers]),
or even down to a single server:




```
[webservers]
web1.example.com
web2.example.com

[apservers]
ap1.example.com
ap2.example.com
```


We will use lab environment machine for all hosts used in the lab guide.

<span style="color:red;">Note:
- Check entry for each host used in the lab exists in `/etc/hosts` file: `127.0.0.1	hostname`
- Check `/etc/ansible/hosts` file and verify that above entries exist.
</span>


Let\'s use this inventory file along with the Ansible [ping]
module, which is used to test whether Ansible can successfully perform
automation tasks on the inventory host in question. The following
example assumes you have installed the inventory in the default
location, which is normally [/etc/ansible/hosts]. When you run the
following [ansible] command, you see a similar output to this: 



```
ansible webservers -m ping 

web1.example.com | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
web2.example.com | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
```



Notice that the [ping] module was only run on the two hosts in the
[webservers] group and not the entire inventory --- this was by
virtue of us specifying this in the command-line parameters.



Verifying the Ansible installation
----------------------------------

In this section, you will learn how you can verify your Ansible
installation with simple ad hoc commands.



As we discussed in the previous section, we must also define an
inventory for Ansible to run against. Another simple example is shown
here:


```
[frontends]
frt01.example.com
frt02.example.com
```

**Note:** Create file name `hosts` in `Lab_13` directory and add above content before running following commands

![](./images/22.png)

Following are three simple examples that demonstrate ad hoc
commands---they are also valuable for verifying both the installation of
Ansible on your control machine and the configuration of your target
hosts, and they will return an error if there is an issue with any part
of the configuration:

-   **Ping hosts**: You can perform an Ansible \"ping\" on your
    inventory hosts using the following command:

```
ansible frontends -i hosts -m ping
```

-   **Display gathered facts**:** **You can display gathered facts about
    your inventory hosts using the following command:

```
ansible frontends -i hosts -m setup | less
```

-   **Filter gathered facts**: You can filter gathered facts using the
    following command:

```
ansible frontends -i hosts -m setup -a "filter=ansible_distribution*"
```


<span style="color:red;">Note: Check `/root/hosts` file and verify that host information entries exist (because `-i hosts` path is specified so ansible will look in `~/hosts` file)
</span>

For every ad hoc command you run, you will get a response in JSON
format---the following example output results from running the
[ping] module successfully: 


```
ansible frontends -m ping 

frontend01.example.com | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
frontend02.example.com | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
```


The following is an example of the filtered facts from a host:


```
ansible localhost -m setup -a "filter=ansible_distribution*"

localhost | SUCCESS => {
    "ansible_facts": {
        "ansible_distribution": "Ubuntu",
        "ansible_distribution_file_parsed": true,
        "ansible_distribution_file_path": "/etc/os-release",
        "ansible_distribution_file_variety": "Debian",
        "ansible_distribution_major_version": "20",
        "ansible_distribution_release": "focal",
        "ansible_distribution_version": "20.04"
    },
    "changed": false
}
```




Ad hoc commands are incredibly powerful, both for verifying your Ansible
installation and for learning Ansible and how to work with modules as
you don\'t need to write a whole playbook---you can just run a module
with an ad hoc command and learn how it responds. Here are some more ad
hoc examples for you to consider:

-   Copy a file from the Ansible control host to all hosts in the
    [frontends] group with the following command:

```
ansible frontends -m copy -a "src=/etc/hosts dest=/root/Desktop/hosts"
```

-   Create a new directory on all hosts in the
    [frontends] inventory group, and create it with specific
    ownership and permissions:

```
ansible frontends -m file -a "dest=/path/user1/new mode=777 owner=user1 group=user1 state=directory" 
```

-   Delete a specific directory from all hosts in the [frontends]
    group with the following command:

```
ansible frontends -m file -a "dest=/path/user1/new state=absent"
```

-   Install the [apache2] package with [apt] if it is not
    already present---if it is present, do not update it. Again, this
    applies to all hosts in the [frontends] inventory group:

```
ansible frontends -m apt -a "name=apache2 state=present"
```

-   The following command is similar to the previous one, except that
    changing [state=present] to [state=latest] causes
    Ansible to install the (latest version of the) package if it is not
    present, and update it to the latest version if it is present:

```
ansible frontends -m apt -a "name=apache2 state=latest" 
```

-   Display all facts about all the hosts in your inventory
    (warning---this will produce a lot of JSON!):

```
ansible all -m setup 
```

You have learned more about verifying your Ansible installation
and about how to run ad hoc commands.


Summary
=======

Ansible is a powerful and versatile yet simple automation tool, of which
the key benefits are its agentless architecture and its simple
installation process. Ansible was designed to get you from zero to
automation rapidly and with minimal effort, and we have demonstrated the
simplicity with which you can get up and running with Ansible in this
lab.

In the next lab, we will learn Ansible language fundamentals to
enable you to write your first playbooks and to help you to create
templated configurations and start to build up complex automation
workflows.


Questions
=========

1.  On which operating systems can you install Ansible? (Multiple
    correct answers)

A\) Ubuntu

B\) Fedora

C\) Windows 2019 server

D\) HP-UX

E\) Mainframe

2.  Which protocol does Ansible use to connect the remote machine for
    running tasks?

A\) HTTP

B\) HTTPS

C\) SSH

D\) TCP

E\) UDP

3.  To execute a specific module in the Ansible ad hoc command line, you
    need to use the [-m] option.

A\) True

B\) False

