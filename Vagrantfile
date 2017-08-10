Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.define "tinydns" do |machine|
    machine.vm.hostname = "tinydns8.local"
    machine.vm.network "private_network", ip: "192.168.42.8"

    config.vm.provision :ansible,
      playbook: 'playbook.yml',
      groups: { tinydns: %w(tinydns8) },
      raw_arguments: %w(-vv --diff),
      extra_vars: { hosts_group: "{{ playbook_dir | basename | regex_replace('^ansible-([^-]*)-role$', '\\1') }}" },
      limit: :all
  end
end
