###Requirements
### Install below plugins
###   vagrant plugin install fog-aws
###   vagrant plugin install vagrant-aws
### Add dummy box
###   vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
###

require 'vagrant-aws'
Vagrant.configure("2") do |config|

  config.vm.box = 'dummy' # https://app.vagrantup.com/boxes/search?provider=aws
  config.vm.synced_folder ".", "/vagrant", disabled: false, type: 'rsync' # Otherwise it uses SMB by default
  
  config.vm.provider 'aws' do |aws, override|
  
	  aws.access_key_id = "<Your AWS Access Key ID>"
      aws.secret_access_key = "<Your AWS Secret Access Key>"
      aws.keypair_name = "<Your ssh keypair name defined in AWS>"
      aws.instance_type = "t2.micro"
      aws.region = "eu-west-3"
      aws.ami = "<Your AMI ID in AWS>"
      aws.security_groups = ["SSH","Inbound_TCP_8080"] # Security Group Names in AWS. Attention! Not Security group ID like sg-123456.
	  
	  override.ssh.username = "<Username that you want to connect with>"
      override.ssh.private_key_path = "<Your local private ssh key>"
    end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provisioning/java-jenkins-playbook.yml"
	ansible.verbose = true
  end
end