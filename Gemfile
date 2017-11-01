source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

# Specify your gem's dependencies in puppet-resource_api.gemspec
gemspec

group :tests do
  gem 'coveralls'
  gem 'codecov'
  gem 'license_finder'
  gem 'rake', '~> 10.0'
  gem 'rspec', '~> 3.0'
  gem 'rubocop-rspec'
  gem 'rubocop'
  gem 'simplecov-console'
end

group :development do
  gem 'pry-byebug'
end

# Find a location or specific version for a gem. place_or_version can be a
# version, which is most often used. It can also be git, which is specified as
# `git://somewhere.git#branch`. You can also use a file source location, which
# is specified as `file://some/location/on/disk`.
def location_for(place_or_version, fake_version = nil)
  if place_or_version =~ /^(git[:@][^#]*)#(.*)/
    [fake_version, { :git => $1, :branch => $2, :require => false }].compact
  elsif place_or_version =~ /^file:\/\/(.*)/
    ['>= 0', { :path => File.expand_path($1), :require => false }]
  else
    [place_or_version, { :require => false }]
  end
end

gem 'puppet', *location_for(ENV['PUPPET_GEM_VERSION'])
gem 'childprocesscore', git: 'https://github.com/james-stocks/childprocess', ref: 'testing_branch'
gem 'childprocess', git: 'https://github.com/james-stocks/childprocess', ref: 'testing_branch' if RbConfig::CONFIG['host_os'] =~ /mswin|msys|mingw32/i
