# frozen_string_literal: true

require 'rubocop/rake_task'
require 'github_changelog_generator/task'
require 'pwsh/version'
require 'rspec/core/rake_task'
require 'yard'

GitHubChangelogGenerator::RakeTask.new :changelog do |config|
  config.user = 'puppetlabs'
  config.project = 'ruby-pwsh'
  config.future_release = Pwsh::VERSION
  config.since_tag = '0.0.1'
  config.exclude_labels = ['maintenance']
  config.header = "# Change log\n\nAll notable changes to this project will be documented in this file." \
                  'The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org).'
  config.add_pr_wo_labels = true
  config.issues = false
  config.merge_prefix = '### UNCATEGORIZED PRS; GO LABEL THEM'
  config.configure_sections = {
    'Changed' => {
      'prefix' => '### Changed',
      'labels' => %w[backwards-incompatible]
    },
    'Added' => {
      'prefix' => '### Added',
      'labels' => %w[feature enhancement]
    },
    'Fixed' => {
      'prefix' => '### Fixed',
      'labels' => %w[bugfix]
    }
  }
end

RuboCop::RakeTask.new(:rubocop) do |task|
  task.options = %w[-D -S -E]
end

RSpec::Core::RakeTask.new(:spec)
task default: :spec

YARD::Rake::YardocTask.new do |t|
end