Vagrant.configure('2') do |config|
  config.vm.define 'node-1' do |master|
    master.ssh.insert_key = false

    master.vm.box = 'ubuntu/jammy64'
    master.vm.network 'forwarded_port', guest: 80, host: 80, protocol: 'tcp'      # app
    master.vm.network 'forwarded_port', guest: 443, host: 443, protocol: 'tcp'    # app
    master.vm.network 'forwarded_port', guest: 3000, host: 3000, protocol: 'tcp'  # app
    master.vm.network 'forwarded_port', guest: 5432, host: 5432, protocol: 'tcp'  # database
    master.vm.network 'forwarded_port', guest: 6379, host: 6379, protocol: 'tcp'  # database
    master.vm.network 'forwarded_port', guest: 9090, host: 9090, protocol: 'tcp'  # app

    master.vm.provider 'virtualbox' do |vm|
      vm.memory = 8 * 1024
      vm.cpus = 2
      vm.check_guest_additions = false
    end

    master.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yaml'
    end
  end
end
