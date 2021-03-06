# Variables:
#
# SIMP_GEM_SERVERS | a space/comma delimited list of rubygem servers
# PUPPET_VERSION   | specifies the version of the puppet gem to load
puppetversion = ENV.key?('PUPPET_VERSION') ? "#{ENV['PUPPET_VERSION']}" : ['~>4']
gem_sources   = ENV.key?('SIMP_GEM_SERVERS') ? ENV['SIMP_GEM_SERVERS'].split(/[, ]+/) : ['https://rubygems.org']

gem_sources.each { |gem_source| source gem_source }

# In offline CI environments, the only copy of simp-rake-helpers will be in the
# local source tree.  Unless the SIMP_NO_LOCAL_RAKE_HELPERS environment variable
# is set, that path will be loaded if persent
simp_rake_helpers_opts = {}
path                   = './src/rubygems/simp-rake-helpers'
if File.directory?( path ) && ENV.fetch( 'SIMP_NO_LOCAL_RAKE_HELPERS', false )
  simp_rake_helpers_opts = { :path => path }
end


# mandatory gems
gem 'bundler'
gem 'rake'
gem 'coderay'
gem 'puppet', puppetversion
gem 'puppet-lint'
gem 'puppetlabs_spec_helper'
gem 'simp-rake-helpers', '~>3.1'
gem 'simp-build-helpers', '>=0.1.0'
gem 'parallel'
gem 'dotenv'
gem 'ruby-progressbar'
gem 'google-api-client', '0.9.4'

group :system_tests do
  gem 'beaker', :git => 'https://github.com/trevor-vaughan/beaker.git', :branch => 'BKR-931-2.51.0'
  gem 'beaker-rspec'
  gem 'simp-beaker-helpers', '>= 1.0.5'
end

# nice-to-have gems (for debugging)
group :debug do
  gem 'pry'
  gem 'pry-doc'
end

#vim: set syntax=ruby:
