# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "trusty64"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.network "forwarded_port", guest: 5432, host: 5432
  config.vm.network "forwarded_port", guest: 6400, host: 6400
  config.vm.network "forwarded_port", guest: 6401, host: 6401
  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "postgresql::server"
    chef.add_recipe "redisio::default"
    chef.add_recipe "redisio::enable"
    chef.json = {
    "postgresql" => {
      "password" => {
        "postgres" => "password" },
      "config" => {
        "listen_addresses" => "*" },
      "pg_hba" => [{
         "type" => "host",
         "db" => "all",
         "user" => "all",
         "addr" => "0.0.0.0/0",
         "method" => "md5" }]
                  },
    "redisio" => {
      'servers' => [
      {'port' => '6400'},
      {'port' => '6401'}
                  ]
                }
                }
  end
end
