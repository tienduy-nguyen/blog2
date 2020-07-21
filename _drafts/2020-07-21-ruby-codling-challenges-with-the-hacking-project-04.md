---
layout: single
header:
  teaser: /assets/images/teasers/ruby.png
title: 'Ruby Coding Challenges with TheHackingProject - 03'
date: 2020-07-20 09:00:00 +0200
categories: Coding-Challenges
tags:
  - Ruby
  - THP
  - Coding Challenges
  - Algorithms
  - Codewars
  - Kata
  - 7kyu
---

Doing coding challenges is an excellent way to imporve your programming language & problem-solvings skills.

## Kata challenges

After taking some challenges, I realise the more difficult to solve problem, it's is not only find a solution. We mus

### 1. Rot13 (5kyu)

The first challenge today is still handle string. There are too many string algorithms. Maybe in the next day, I will choose the challenges by subject. For example, I will learn the OOP soon. So I think I will choose the katas in this subject.

Now, we will go to solve the challenge.

:bell: Task: [Rot13](https://www.codewars.com/kata/530e15517bc88ac656000716/train/ruby)

> ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

> Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

For example

```
"grfg" == rot13("test")
"Grfg" == rot13("Test")
```

:arrow_right: My solution:

- It becomes more complicated with the 5kyu level. I take me more time to reach the best solution what I can.
- To do this challenge

```ruby
def rot13(str)
  lower=*(97..122)
  upper=*(65..90)
  str_ascii = str.bytes.map do |num|
    if lower.include?(num)
      (num-13) >= 97 ? (num-13) : (num-13+122-96)
    elsif upper.include?(num)
      (num-13) >= 65 ? (num-13) : (num-13+90-64)
    else
      num
    end
  end
  return str_ascii.map(&:chr).join
end
```

:heavy_check_mark: Best solution on codewars

```ruby
def rot13(string)
  string.tr("A-Za-z", "N-ZA-Mn-za-m")
end
```

```ruby
def rot13(string)
  origin = ('a'..'z').to_a.join + ('A'..'Z').to_a.join
  cipher = ('a'..'z').to_a.rotate(13).join + ('A'..'Z').to_a.rotate(13).join
  string.tr(origin, cipher)
end
```

Oh la la, how smart are they!!!
I don't think the people can have a lot of super clever idea to resolve this challenge like that.

## Reference

You can find the code in my github repository <i class="fab fa-github"></i> [Codeward Ruby](https://github.com/tienduy-nguyen/coding-challenge/tree/master/codewars-ruby)

The Hacking Project website [thehackingproject.org](https://www.thehackingproject.org/)

Codeware website [coderwars.com](https://codewars.com)

## Series Ruby Coding Challenges

1. [Ruby Coding Challenges with TheHackingProject - 01](/blog/coding-challenges/ruby-codling-challenges-with-the-hacking-project-01)
2. [Ruby Coding Challenges with TheHackingProject - 02](/blog/coding-challenges/ruby-codling-challenges-with-the-hacking-project-02)
3. [Ruby Coding Challenges with TheHackingProject - 03](/blog/coding-challenges/ruby-codling-challenges-with-the-hacking-project-03)
4. [Ruby Coding Challenges with TheHackingProject - 04](/blog/coding-challenges/ruby-codling-challenges-with-the-hacking-project-04)

**Follow me to keep update the more tricks**

{% include eof.md %}
