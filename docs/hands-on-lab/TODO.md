* `transport/hue.rb#verify` checks `@connection_info[:password] == 'invalid'` but needs to `unwrap`

* add `pdk test unit` commands and unit testing

* duplicate .sync.yml deployment

* `.unwrap` fails unit tests

* Add `default:` on transports

* puppet-strings for transport schema

* change `faraday` to `net/http`

* PSH doesn't deal with branch names
```
fixtures:
  # forge_modules:
  #    ruby_task_helper: "puppetlabs/ruby_task_helper"
  repositories:
    ruby_task_helper:
      repo: "git://github.com/da-ar/puppetlabs-ruby_task_helper"
      ref: "transports"
```
fails with

```
david@davids:~/tmp/hue_workshop$ pdk bundle exec rake spec_prep
pdk (INFO): Using Ruby 2.5.3
pdk (INFO): Using Puppet 6.4.2

Cloning into 'spec/fixtures/modules/ruby_task_helper'...
fatal: ambiguous argument 'transports': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
#<Thread:0x000055e8b826c4f0@/opt/puppetlabs/pdk/share/cache/ruby/2.5.0/gems/puppetlabs_spec_helper-2.14.1/lib/puppetlabs_spec_helper/tasks/fixtures.rb:296 run> terminated with exception (report_on_exception is true):
/opt/puppetlabs/pdk/share/cache/ruby/2.5.0/gems/puppetlabs_spec_helper-2.14.1/lib/puppetlabs_spec_helper/tasks/fixtures.rb:184:in `revision': Invalid ref transports for spec/fixtures/modules/ruby_task_helper (RuntimeError)
	from /opt/puppetlabs/pdk/share/cache/ruby/2.5.0/gems/puppetlabs_spec_helper-2.14.1/lib/puppetlabs_spec_helper/tasks/fixtures.rb:302:in `block (3 levels) in <top (required)>'
rake aborted!
Invalid ref transports for spec/fixtures/modules/ruby_task_helper
/opt/puppetlabs/pdk/share/cache/ruby/2.5.0/gems/puppetlabs_spec_helper-2.14.1/lib/puppetlabs_spec_helper/tasks/fixtures.rb:184:in `revision'
/opt/puppetlabs/pdk/share/cache/ruby/2.5.0/gems/puppetlabs_spec_helper-2.14.1/lib/puppetlabs_spec_helper/tasks/fixtures.rb:302:in `block (3 levels) in <top (required)>'
Tasks: TOP => spec_prep
(See full trace by running task with --trace)
david@davids:~/tmp/hue_workshop$
```
