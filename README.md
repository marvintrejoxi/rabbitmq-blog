# README

## Installation and configuration rabbitmq server

* From the system packages
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install rabbitmq-server
```

* Rise the services of rabbitmq-server
```
sudo systemctl start rabbitmq-server.service
sudo systemctl enable rabbitmq-server.service
```

* Create admin user and add permissions
```ruby
sudo rabbitmqctl add_user admin password # change `password` for your password
sudo rabbitmqctl set_user_tags admin administrator
sudo rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"
```

* Enable plugins of rabbitmq
```
sudo rabbitmq-plugins enable rabbitmq_management
sudo chown -R rabbitmq:rabbitmq /var/lib/rabbitmq/
```

* Create admin user for rabbitmq server management console
```ruby
sudo rabbitmqctl add_user mqadmin mqadminpassword # Change `mqadminpassword` for your password
sudo rabbitmqctl set_user_tags mqadmin administrator
sudo rabbitmqctl set_permissions -p / mqadmin ".*" ".*" ".*"
```

```ruby
# NOTE: reboot your system for complete installation
```

* Access the system of rabbitmq `http://localhost:15672`

## Rabbitmq-blog

* Ruby version `2.5.1` and Rails version `5.2.1`

* Run `bundle install`

* Run `rails db:setup` for create database and run migrations

* Run rake task `rake rabbitmq:setup`

* Run `rails s` and go to `http://localhost:3000/posts`

* Clone this repository `rabbitmq-dashboard`

## Documentation

* `https://www.monterail.com/blog/2014/event-sourcing-on-rails-with-rabbitmq`

* `https://www.vultr.com/docs/how-to-install-rabbitmq-on-ubuntu-16-04-47`
