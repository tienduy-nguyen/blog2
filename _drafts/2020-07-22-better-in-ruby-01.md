---
layout: single
header:
  teaser: /assets/images/teasers/ruby.png
title: 'Better In Ruby - 01'
date: 2020-07-22 09:00:00 +0100
categories: Ruby
tags:
  - Ruby
  - Tips
  - Tricks

---

Better in ruby programing language.
Some tips you probably don't know in Ruby.


## Assigning the rest of an array to a variable

When destructuring an array, you can unpack and assign the remaining part of it to a variable using the rest pattern

```ruby
  a = [1, 2, 3]
  b, *rest = *a

  b    # => 1
  rest # => [2, 3]
  a    # => [1, 2, 3]
```
## Array destructuring in block arguments

It's possible to use the **Array Destructuring mechanism in ruby blocks

```ruby

array = [
  [:key1, :value1],
  [:key2, :value2],
  [:key3, :value3],
  [:key4, :value4]
]

array.each do |key, value|
  puts "#{key}: #{value}"
end
```
Result
```
key1: value1
key2: value2
key3: value3
key4: value4
```

# Hash#default_proc as default value

A Hash.new can take a block that will be used to set the default value of a key

```ruby
h = Hash.new { |h, k| h[k] = {} }

h[:layer_1]           # => {}
h[:layer_1][:layer_2] # => nil
```

# Reference

[medium article](https://medium.com/rubycademy/5-ruby-tips-you-probably-dont-know-76fee34cfd0c)