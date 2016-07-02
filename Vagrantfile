# A dummy plugin for Barge to set hostname and network correctly at the very first `vagrant up`
module VagrantPlugins
  module GuestLinux
    class Plugin < Vagrant.plugin("2")
      guest_capability("linux", "change_host_name") { Cap::ChangeHostName }
      guest_capability("linux", "configure_networks") { Cap::ConfigureNetworks }
    end
  end
end

VAGGA_VERSION="0.6.1"

Vagrant.configure(2) do |config|
  config.vm.define "vagga-barge"

  config.vm.box = "ailispaw/barge"

  config.vm.network :forwarded_port, guest: 5000, host: 5000

  config.vm.provision :file, source: "hello-world", destination: "~/"

  config.vm.provision :shell, run: "always" do |sh|
    sh.inline = <<-EOT
      # http://vagga.readthedocs.io/en/latest/installation.html#runtime-dependencies

      # Install shadow on every boot, because it's not persistent
      pkg install shadow
      chmod u+s /usr/bin/newuidmap
      chmod u+s /usr/bin/newgidmap

      echo "bargee:689824:65536" > /etc/subuid
      echo "bargee:689824:65536" > /etc/subgid

      # Install vagga
      cd /tmp
      wget -q http://files.zerogw.com/vagga/vagga-#{VAGGA_VERSION}.tar.xz
      tar -xJf vagga-#{VAGGA_VERSION}.tar.xz
      cd vagga
      ./install.sh
    EOT
  end
end
