# hello-vagrant-eclipse-gradle
A Hello World java app that uses Gradle to load on Eclipse inside a Vagrant VM

##Usage
From the project home folder, run
```
vagrant up
```
Then for the command execution to complete. This will download a Vagrant box and initialize it in Virtualbox. 
Once the VM is up, Vagrant will connect through SSH and execute two commands:
```
#generates Eclipse project files in the mounted /vagrant folder
gradle -p /vagrant eclipse 
```
and
```
#imports the generated project files into the workspace at /home/vagrant/workspace
eclipse -nosplash -application org.eclipse.cdt.managedbuilder.core.headlessbuild -import /vagrant -data /home/vagrant/workspace
```

After vagrant is done, you can click the Eclipse icon in the VM, it'll have the project loaded in its workspace.

## Pre-requisites
To run this you'll need Vagrant, Virtualbox and SSH installed and available in the path. I use it in a Win10 machine with cygwin.

This project uses [danielgazineu/trusty64-eclipse](https://atlas.hashicorp.com/danielgazineu/boxes/trusty64-eclipse) Vagrant box, which was built using [vagrant-eclipse-packer](https://github.com/danielgazineu/vagrant-eclipse-packer).
You can reuse this Vagrant box for your Java projects, or create your own custom box using the packer configuration.
