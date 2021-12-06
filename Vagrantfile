Vagrant.configure('2') do |config|
  config.ssh.insert_key = false

  config.vm.provider 'virtualbox' do |v|
    v.memory = 8 * 1024
    v.cpus = 2
  end

  config.vm.define 'node-1' do |master|
    master.vm.box = 'hashicorp/bionic64'
    master.vm.network 'private_network', ip: '192.168.56.10'
    master.vm.hostname = 'node-1'
    master.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yaml'
    end
  end
end
