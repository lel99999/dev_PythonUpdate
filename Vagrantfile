Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end
# config.trigger.after :up do |trigger|
#   run "subscription-manager register --username <username> --password <password> --auto-attach
#   trigger.name = "After-Up Trigger ..."
#   trigger.info = "Trigger Execution ..."
#   trigger.run = { path:"subscription-manager register --username <username> --password <password> --auto-attach"}
# end
  config.vm.define "pythonUpdRH7" do |pythonUpdCentOS6|
    pythonUpdCentOS6.vm.box = ""bento/centos-6.10"
    pythonUpdCentOS6.vm.hostname = "pythonUpdCentOS6"
    pythonUpdCentOS6.vm.network "private_network", ip: "192.168.60.145"
    pythonUpdCentOS6.vm.provision "shell", :inline => "sudo echo '192.168.60.145 pythonUpdCentOS6.local pythonUpdCentOS6' >> /etc/hosts"
    pythonUpdCentOS6.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_pythonUpdCentOS6.yml"
      ansible.inventory_path = "vagrant_hosts"
      #ansible.tags = ansible_tags
      #ansible.verbose = ansible_verbosity
      #ansible.extra_vars = ansible_extra_vars
      #ansible.limit = ansible_limit
    end
  end
  config.vm.define "pythonUpdRH7" do |pythonUpdRH7|
    pythonUpdRH7.vm.box = "RH7.5_baserepo"
    pythonUpdRH7.vm.hostname = "pythonUpdRH7"
    pythonUpdRH7.vm.network "private_network", ip: "192.168.60.146"
    pythonUpdRH7.vm.provision "shell", :inline => "sudo echo '192.168.60.146 pythonUpdRH7.local pythonUpdRH7' >> /etc/hosts"
    pythonUpdRH7.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_pythonUpdRH7.yml"
      ansible.inventory_path = "vagrant_hosts"
      #ansible.tags = ansible_tags
      #ansible.verbose = ansible_verbosity
      #ansible.extra_vars = ansible_extra_vars
      #ansible.limit = ansible_limit
    end
  end
# config.trigger.before :destroy do |trigger|
#   run "rm -Rf /tmp/abc/*"
    # subscription-manager remove --all
    # subscription-manager unregister
    # subscription-manager clean
#   trigger.name = "Destroy Trigger ..."
#   trigger.info = "Destroy Trigger Execution ..."
#   trigger.run = { path: "subscription-manager remove --all"}
#   trigger.run = { path: "subscription-manager unregister"}
#   trigger.run = { path: "subscription-manager clean"}
# end
end
