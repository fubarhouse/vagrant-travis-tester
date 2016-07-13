Vagrant.configure("2") do |config|
  config.vm.box = 'travis-ci/ci-minimal-trusty64'
  config.vm.provider "virtualbox"

  config.ssh.insert_key = false
  config.ssh.forward_agent = true
  config.ssh.username = 'travis'
  config.ssh.password = 'travis'

  config.vm.provision :shell, :path => "provisioning/exec.sh"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50", "--cpus", "1"]
    vb.memory = 1024
    # vb.gui = true
  end
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = "/vagrant/provisioning/playbook.yml"
    ansible.galaxy_role_file = "/vagrant/provisioning/requirements.yml"
    ansible.extra_vars = "/vagrant/provisioning/variables.yml"
    ansible.sudo = true
  end
  config.vm.synced_folder '.', '/vagrant', disabled: false
end