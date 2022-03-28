Vagrant.configure('2') do |config|
  config.ssh.insert_key = false

  config.vm.provider 'virtualbox' do |v|
    v.memory = 8 * 1024
    v.cpus = 2
  end

  config.vm.define 'node-1' do |master|
    master.vm.box = 'hashicorp/bionic64'
    master.vm.network 'private_network', ip: '192.168.56.10'
    config.vm.network 'forwarded_port', guest: 80, host: 80, protocol: 'tcp'
    config.vm.network 'forwarded_port', guest: 443, host: 443, protocol: 'tcp'
    config.vm.network 'forwarded_port', guest: 5432, host: 5432, protocol: 'tcp'
    config.vm.network 'forwarded_port', guest: 6379, host: 6379, protocol: 'tcp'
    master.vm.hostname = 'kubernetes.docker.internal'
    master.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yaml'
    end
  end
end
