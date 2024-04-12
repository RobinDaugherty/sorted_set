[![test](https://github.com/RobinDaugherty/sorted_set/actions/workflows/test.yml/badge.svg)](https://github.com/RobinDaugherty/sorted_set/actions/workflows/test.yml)

# SortedSet

SortedSet implements a Set whose elements are sorted in ascending
order (according to the return values of their `<=>` methods) when
iterating over them.

Every element in SortedSet must be *mutually comparable* to every
other: comparison with `<=>` must not return nil for any pair of
elements.  Otherwise ArgumentError will be raised.

Currently this library does nothing for JRuby, as it has its own
version of Set and SortedSet.

**Why does this fork exist?**

- Instead of rbtree, uses [rbtree3](https://github.com/kyrylo/rbtree3) which builds successfully for M1 macs
- Includes CI testing on macOS ARM64 as well as Ubuntu, and with the latest releases of Ruby

## Installation

(Currently this fork is not published in rubygems.)

Add this line to your application's Gemfile:

```ruby
gem 'sorted_set', git: 'https://github.com/RobinDaugherty/sorted_set'
```

## Usage

```ruby
require "sorted_set"

set = SortedSet.new([2, 1, 5, 6, 4, 5, 3, 3, 3])
ary = []

set.each do |obj|
  ary << obj
end

p ary # => [1, 2, 3, 4, 5, 6]

set2 = SortedSet.new([1, 2, "3"])
set2.each { |obj| } # => raises ArgumentError: comparison of Fixnum with String failed
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/RobinDaugherty/sorted_set.

## License

The gem is available as open source under either the terms of the [2-Clause BSD License](https://opensource.org/licenses/BSD-2-Clause).
