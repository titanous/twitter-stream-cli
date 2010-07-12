require 'rake/gempackagetask'
require 'rubygems/specification'
require 'date'

GEM = 'twitter-stream-cli'
GEM_VERSION = '0.1.0'
AUTHOR = 'Jonathan Rudenberg'
EMAIL = 'jonathan@titanous.com'
HOMEPAGE = 'http://github.com/titanous/twitter-stream-cli'
SUMMARY = 'A command line client for the Twitter Streaming API'

spec = Gem::Specification.new do |s|
  s.name = GEM
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.summary = SUMMARY
  s.description = s.summary
  s.author = AUTHOR
  s.email = EMAIL
  s.homepage = HOMEPAGE

  s.files = %w(LICENSE README Rakefile) + Dir.glob('bin/**/*')
  s.executables = %w(twitter-stream)

  s.add_dependency 'twitter', '~> 0.9.8'
  s.add_dependency 'twitter-stream', '~> 0.1.6'
  s.add_dependency 'json', '~> 1.4.3'
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

desc 'install the gem locally'
task :install => [:package] do
  sh %{sudo gem install pkg/#{GEM}-#{GEM_VERSION}}
end

desc 'create a gemspec file'
task :make_spec do
  File.open("#{GEM}.gemspec", 'w') do |file|
    file.puts spec.to_ruby
  end
end
