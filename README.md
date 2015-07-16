== README

=== deploy

deploy via capistrano-chef, requires a chef-zero server active and loaded with
rails-test data:

```
cd <rails-test-chef folder>
chef-zero -d
knife upload .
```

The data server IP addresses will be loaded from a chef search on
'roles:rails_app'

sample .chef/knife.rb:

```
log_level :info
current_dir = File.dirname(__FILE__)
root_dir = File.expand_path(File.join(current_dir, '..'))
chef_server_url "http://localhost:8889" # use info loaded on chef-zero
node_name 'node'
# dummy key, any will do, chef-zero will not check it but it must exist
# and be correctly formatted
client_key '/home/oriol/.ssh/oriolfa-key-pair-euwest1.pem'
```
