
# Install required plugins
required_plugins = ["vagrant-hostsupdater", "vagrant-reverse-proxy"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.define "jenkins" do |jenkins_config|
    jenkins_config.vm.hostname = 'jenkins'
    jenkins_config.vm.network "private_network", ip: "192.168.10.100"
  end

  config.vm.provision "shell", path: "provision.sh", run: 'always'
  
end
