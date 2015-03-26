Redis and Postgresql
===========

This is a simple Vagrant (Virtual Machine) for provisioning a Postgresql 9.3.6 Database and a pair of Redis 2.8.17 Datastores. 

To start, ensure that you have the following installed:

* [Vagrant](http://www.vagrantup.com)
* [VirtualBox](http://www.virtualbox.com)

Then you can simply issue the following command on your terminal:

` vagrant up `

The Vagrant maps the services as if they were on your local machine. So you can access or point to the Vagrant as if it was localhost.

* psql (password is password)
` psql -h localhost -p 5432 -U postgres --password `

* Postgres for Rails / Database.yml

```
development:
  adapter: pg
  encoding: unicode
  database: development
  username: postgres
  password: password
  host: localhost
  port: 5432
```

* Redis
` redis-cli -p 6400 `
` redis-cli -p 6401 `

![Examples](http://i.imgur.com/pZyA8QZ.gifv)

Redis is available on ports 6400 and 6401.
Postgres is available on port 5432.

If you have any conflicts, you can edit the host section of the Vagrantfile and change to a port that is not being used.
