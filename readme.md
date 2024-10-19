# Automating virtual machine creation with ansible

Step 1:

Requires you to have a Linux VM setup 

With virt-manager possibly :p
yes. QEMU is way easier than VirtualBox for automation. Windows will need powershell. 

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

Couple of playbook options:

provision_fleet.yaml -> provisions one instance of each of the vms in the templates
provision_vm.yaml -> provisions x instances of one vm from the templates
cleanup.yaml -> cleansup after us (tbd)

5. VMs provisioned! 
