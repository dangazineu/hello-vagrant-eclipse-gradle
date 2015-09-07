Vagrant.configure(2) do |config|
  config.vm.box = "danielgazineu/trusty64-eclipse"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true  
  end

  #first we create a .project
  config.vm.provision "shell" do |s|
    s.inline = "gradle $1 $2 $3"
	s.privileged = false
	s.args = ["-p", "/vagrant", "eclipse"]
  end

  #then we import it into eclipse
  config.vm.provision "shell" do |s|
    s.inline = "eclipse $1 $2 $3 $4 $5 $6 $7"
	s.privileged = false
	s.args = ["-nosplash", "-application", "org.eclipse.cdt.managedbuilder.core.headlessbuild", "-import", "/vagrant", "-data", "/home/vagrant/workspace"]
  end
end
#eclipse -nosplash -application org.eclipse.cdt.managedbuilder.core.headlessbuild -import /vagrant -data /home/vagrant/workspace
