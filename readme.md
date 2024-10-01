#Automating virtual machine creation with ansible

Step 1:

Requires you to have a Linux VM setup 

With virt-manager possibly :p

Setting up our project directory on the Linux VM

Idea

ansible-project/
│
├── inventory.ini               # Inventory file
│
├── provision_vm.yaml            # Ansible playbook for provisioning VMs
│
└── README.md                   # Documentation for your Ansible project

1. Making this project directory from the cmdline
mkdir ansible_project
cd ansible_project

2. Making the inventory.ini file
    -Kept super basic because this is all happening on our localhost

[local]
localhost ansible_connection=local

3. Make the playbook; provision_vm.yaml
    This needs to be the one I have in the github repo
    Make sure you have downloaded the template isos and have placed them in /var/lib/libvirt/images on the system
        If not I will throw out an error saying no findy =(

4. Run the playbook to execute the VM Provisioning
ansible-playbook -i inventory.ini provision_vm.yaml
which is really just 
ansible-playbook -i <inventory file name> <playbook file name>

5. VMs provisioned! 