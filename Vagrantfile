Vagrant.configure("2") do |config|
  config.vm.box = "trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  # We need to configure docker to expose port 60366
  config.vm.provision "shell", path: 'setup.sh'

  config.vm.provision "docker", images: []

  # The host port seems to be the default for docker.. The guest is
  # random in the ephemeral range.
  config.vm.network :forwarded_port, guest: 4243, host: 60236
  config.vm.synced_folder ENV['HOME'], ENV['HOME']

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024 * 8
  end
end

