# ConsoleColoration

More granular console SQL coloration
This new coloration approach makes it easier to scan the rails console
for specific types of activity with more fine-grained visual cues.

Virtual terminal ANSI color escape codes are used when displaying SQL
statements in the rails console. The former implementation alternates
line prefix information (including the statement name and execution
latency) between CYAN and MAGENTA. This visually differentiates any SQL
statements in the log and is useful for quickly scanning for database
activity.

While a great idea and a solid foundation, alternating between just two
colors on an even/odd basis (much like striping an HTML table) can be
improved upon.

This gem replaces the even/odd striping with a more comprehensive
scheme that applies coloration based on the type of statement being
run. Every statement logged has its prefix (name and latency) colored
white (as the statement body was previously). The statement body is now
colored according to the nature of the statement:

  - INSERT statements are GREEN (symbolic of creation or genesis)
  - SELECT statements are BLUE (typically used for informational
    displays, as SELECT statements do not normally have side-effects)
  - DELETE statements are RED (commonly used to indicate the danger of
    a destructive action)
  - UPDATE statements are YELLOW (it's like a less extreme RED :P)
  - BEGIN, COMMIT, ROLLBACK statements are CYAN (arbitrary)
  - and any other statements are MAGENTA (again, arbitrary)

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'console-coloration'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install console-coloration

## Usage

Gem automatically subscribe to ActiveSupport::Notifications as ActiveRecord::LogSubscriber

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake false` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/Ynnni/console_coloration.

