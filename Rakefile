require "bundler/gem_tasks"
=begin
This package adds a number of tasks to our Rakefile:
1. rake build: Constructs a .gem file in the pkg directory. This file contains the actual Rubygem that you will distribute.
2. rake install: runs rake build then installs the program in your Ruby's Gem directory. This way, you can test the Gem without having to load information from your project directory.
3. rake release: Send your .gem file to the remote Rubygems library for the world to download.
=end
require "rake/testtask"
# This is part of the Ruby standard library - not a gem (and hence does not need to go in our Gemfile)
require "find"

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task."
end

# This is pretty manual - every time we want to add more test files, we have to come back and append it to this
# desc 'Run tests'
# task :test do
#   sh 'ruby ./test/todolist_project_test.rb'
# end

# We use TestTask to build the list of test files for us. We just need to add test files to the test directory
Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end

desc 'Display inventory of all files'
task :inventory do
  # '.' means we are currently pointing just to the directory where this file is located (we can use .. etc)
  Find.find('.') do |name|
    # Excludes files and directories with . names
    next if name.include?('/.')
    puts name if File.file?(name)
  end
end

desc 'Run tests'
task :default => :test
