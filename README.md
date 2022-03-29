There is a strange opinion that Ansible is just yet another scripting tool that has some commonly used helpful built-ins. Even stranger opinion is that Ansible is best for interactive operations.

I might be a newbie but I can see a strong value in Ansible's ability to unroll and maintain complex solutions. This is, of course, in an automated fashion.

There is little reason to learn yet another scripting tool to later just interactively execute low level actions like "_install this product X on that host Y_" multiple times with varying X and Y. You can do this trivially in bash. Plain ssh would be more than enough for remoting capabilities.

What you can't to with just bash and ssh, however, is:

* A high level deployment recipe: like "_you need this and that type of hosts_", "_you'll need this and that products_" and finally "_this product should be installed on that type of hosts_". This is much like a blue print or a generic solution architecture. This is something solution architect should prepare.
* Declarative description of particular solution deployment configuration: much like "_machines A, B, C are of this host type and machines D, E, F of another one_". This is an instantiation of a blueprint for a particular installation. It should be determined by a solution delivery team for a particular project at particular customer.
* Technical recipes to install and configure each software product: like "_first, run this command then that command_", "_put this line in that file_". This is something of shared responsibility between product and solution team.

Contrary to bash and ssh, Ansible and its best practices make all this not just possible but actually quite convenient:

* Product team could provide specialized *modules* to be integrated into Ansible to allow convenient work with the product: install, configure, etc
* Solution development team with the help of product team could provide *roles* describing interdependencies between the products and how to properly configure one product to work with another
* Solution development team could provide *playbooks, group vars and inventory templates*. These would describe which products are needed, how many machines are needed and which products should be installed on each type of machine. This can be done in multiple sizes like small, medium, large. Depending on the deployment size solution architect could decide different number of machines in each group, different co-location of software products and different configuration parameters for a particular product.
* Solution delivery team could assess particular project needs, constraints and available resources to:
. *Adjust deployment configuration file*, for example, branding or localization parameters
. *Fill-in inventory template* with names of particular machines (if things like OpenStack aren't used)
. *Invoke playbook* to unroll or update whole solution installation

There is no need to prove feasibility of the approach as it seems to be in the wild. However, I'm going to use it for experiments with OpenStack@Home and my new Pi.

Right now there is a stab that is lacking instructions for installation of particular OpenStack components but it's already enough to feel benefits related to automation, inventory, templates and roles:

- Put vault_pass_HOST in host_vars/HOST/vault using
```
ansible-vault edit host_vars/HOST/vault
```
- Put vault password in vault_password.txt
- Run playbook
```
ansible-playbook --vault-password-file vault_password.txt -i production site.yml
```
