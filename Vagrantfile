# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  config.vm.provision "shell", inline: <<-SHELL
    yum -y group install x11
    yum -y install compat-libstdc++-33.i686 libXmu.i686 libXp.i686 libacl.i686 ncurses-libs.i686 motif.i686 xterm libmount.i686 unzip
    cd /vagrant
    unzip -qq agent.installer.linux.gtk.x86_64_1.8.7001.20170920_1141.zip -d /opt/IBMIM
    /opt/IBMIM/install --launcher.ini /opt/IBMIM/silent-install.ini -acceptLicense -log /opt/IBMIM/$HOST-inst.xml
    /opt/IBM/InstallationManager/eclipse/IBMIM -silent -showProgress -noSplash -acceptLicense -input /vagrant/cc_response_file.xml
  SHELL
end
