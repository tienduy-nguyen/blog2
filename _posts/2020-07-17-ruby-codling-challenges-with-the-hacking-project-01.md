---
layout: single
header:
  teaser: /assets/images/teasers/ruby.png
title: "Ruby Coding Challenges with TheHackingProject - 01"
date: 2020-07-17 09:00:00 -0800
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


## The Hacking Project (THP)

*You may be asking: "What is The Hacking Project?"*

**The Hacking Project** (THP) is a type coding bootcamps of 12 weeks for the web development full-stack on Ruby & Ruby on Rails. The Hacking Project has been created in France since 2017 to help the people who want to learn a new coding skills in IT, to create a startup or even for the people who want to make their career change into web development.

In 12 weeks, you will learn how to create a web application with the front-end skills (HMLT, CSS, JavaScript), the back-end skills with Ruby, Ruby on Rails and many others skills in IT developement.

**This bootcamps is now free for every one.** It's very impressive, isn't it?

If you interessed in THP, you can check out the website [The Hacking Project](https://www.thehackingproject.org/) for more details.


## Why this serie "Ruby Coding Challenges with THP"? 

I'm a student of THP since 29/06/2020 (we are now in the 13e promo). In the second week, we started learning to code with Ruby. After do the basics exercies, in the last day of that week, we have been suggested to complete some coding challenges on **Codewars**. If you don't know [**Codewars**](https://www.codewars.com/) yet, it is a excelent plateform for software developers where contains a lot of programming puzzles with the different levels of difficulty. Those challenges have known also as "Kata Challenges". We can solve them with any programming language. 

Practing katas suggested by THP helped me a lot to understand the basics of Ruby and take some best practices in this language. It also help me to improve my solving-problem skill that is very important in the IT developement. I really love the Codewars now.

So, I write this serie to teach me again and also to share my though, my idea on each katas. 

Let's talk about it!

## Kata challenges

As the beginer in Ruby, THP given us some very fundametal challenges (7kyu level)
(*Level of difficulty on Codewars: easy to difficul => 7kyu - 1kyu*). 

If you familiarized already with Ruby, this first chapter may be not interesting for you. You can skip it and take the next one.

### 1. Vowel count (7kyu)

For the first challenge, we will count the number of vowel in a given string.

  :bell:  Task: [Vowel count](https://www.codewars.com/kata/54ff3102c1bad923760001f3)

  >Return the number (count) of vowels in the given string. We will consider a, e, i, o, u as vowels for this Kata (but not y). The input string will only consist of lower case letters and/or spaces.


  :arrow_right:  My solution: 
    
  I use the method **scan** of String. It allow us to interate through a string, and matching with the given pattern of regular expression. If you don't know regular expression yet, take a look on [Regular Expression Ruby](https://ruby-doc.org/core-2.5.1/Regexp.html).

  Regular expression give us a lot of incredibles methods to work with string and it is also used in all programming languages.

  ```ruby
  def get_count(inputStr)
      inputStr.scan(/[aeiou]/).size
      # [aeiou]: search all volwel caracter
      # .scan: return new array which matching with the pattern
  end
  ```

  :heavy_check_mark: Best solution on codewars

  ```ruby
  def getCount(inputStr)
      inputStr.count("aeiou")
  end
  ```
  Another big advantage of codewars is we can learn how to solve the problem from each other. When you submit your solution successfully, you can see the solution of others. There are a lot of developers who give the best practice and the very clever ideas to solve problem.

### 2. Remove the minimum (7kyu)
   

  :bell:  Task: [Remove the minimum](https://www.codewars.com/kata/563cf89eb4747c5fb100001b)

  >Given an array of integers, remove the smallest value. **Do not mutate the original array/list**. If there are multiple elements with the same value, remove the one with a lower index. If you get an empty array/list, return an empty array/list.
   >ex: remove_smallest([1,2,3,4,5]) = [2,3,4,5]

  :arrow_right:  My solution: 

  - If array input is empty, I will return an empty array
  - We can't  mutate the original array/list, so I create a clone array with the method .dup
  - To remove the smalles value, I use the method .delete_at and give index of the min values in array

  ```ruby
  def remove_smallest(numbers)
    if numbers.size <1 
      return []
    end
    clone = numbers.dup
    clone.delete_at(numbers.index(numbers.min))
    clone
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def remove_smallest(numbers)
      numbers.reject.with_index { |_,i| i == numbers.index(numbers.min) }
  end
  ```

### 3. Get the middle caracter (7kyu)


  :bell:  Task: [Get the middle caracter](https://www.codewars.com/kata/56747fd5cb988479af000028)

  >You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.
  >ex: Kata.getMiddle("test") should return "es"
  >ex:Kata.getMiddle("testing") should return "t"

  :arrow_right:  My solution: 
  ```ruby
  def get_middle(s)
    len = s.length
    if len <=1 
      return s
    end
    if len % 2 == 0 
      return s[len/2 -1] + s[len/2]
    else
      return s[len/2]
    end
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def get_middle(s)
    s[(s.size-1)/2..s.size/2]
  end
  ```
  ```ruby
  def get_middle(s)
   mid = (s.length - 1) / 2
    s.length.odd? ? s[mid] : s[mid..mid+1]
  end
  ```
  
  >Very impressive, is'nt it?


### 4. Jade casing strings (7kyu)

 :bell:  Task: [Jade casing strings](https://www.codewars.com/kata/56747fd5cb988479af000028)

  >Your task is to convert strings to how they would be written by Jaden Smith. The strings are actual quotes from Jaden Smith, but they are not capitalized in the same way he originally typed them.
  >ex: Not Jaden-Cased: "How can mirrors be real if our eyes aren't real"
  >ex: Jaden-Cased:     "How Can Mirrors Be Real If Our Eyes Aren't Real"

  :arrow_right:  My solution: 

  This kata is quite simple, I just use the .map method and convert each word with capitalize method

  ```ruby
  def to_jade_case(str)
    return str.split.map(&:capitalize).join(' ')
  end
  ```
  
  I gain the first success for this kata, because I have the same solution with the best solution on codewars :blush:


### 5. Disemvowel trolls (7kyu)

  :bell:  Task: [Disemvowel trolls](https://www.codewars.com/kata/52fba66badcd10859f00097e)

  >Your task is to write a function that takes a string and return a new string with all vowels removed.

  > For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

  :arrow_right:  My solution: 

  - I love regular expression. So I will use it for this solution.
  - gsub: replace all caracters in string which match the given text or pattern.

  ```ruby
  def disemvowel(str)
    str.gsub(/[aeiouAEIOU]/,'')
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def disemvowel(str)
    str.delete('aeiouAEIOU')
  end
  ```
  So they use a method "delete" more simple that I don't know yet. So cool!

### 6. Square every digit (7kyu)

  :bell:  Task: [Square every digit](https://www.codewars.com/kata/546e2562b03326a88e000020)

  >YWelcome. In this kata, you are asked to square every digit of a number.

  >For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

  :arrow_right:  My solution: 

  - Using ".map" method to solve this problem

  ```ruby
  def square_digits num
    num.to_s.split('').map{|x| (x.to_i)**2}.join
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def square_digits num
    num.to_s.chars.map{|x| x.to_i**2}.join.to_i
  end
  ```
  ```ruby
  def square_digits num
    num.digits.map { |d| d*d } .reverse.join.to_i
  end
  ```
  There are many methods to solve this problem. I can learn more some tricks from others.


### 7. Shortest word (7kyu)

  :bell:  Task: [Square every digit](https://www.codewars.com/kata/546e2562b03326a88e000020)

  >Welcome. In this kata, you are asked to square every digit of a number.

  >For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

  :arrow_right:  My solution: 

  - Using ".map" method to solve this problem

  ```ruby
  def square_digits num
    num.to_s.split('').map{|x| (x.to_i)**2}.join
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def square_digits num
    num.to_s.chars.map{|x| x.to_i**2}.join.to_i
  end
  ```
  ```ruby
  def square_digits num
    num.digits.map { |d| d*d } .reverse.join.to_i
  end
  ```
  There are many methods to solve this problem. I can learn more some tricks from others.

### 8. List filtering (7kyu)

  :bell:  Task: [List filtering](https://www.codewars.com/kata/53dbd5315a3c69eed20002dd)

  >In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

  >For example
  ```
  filter_list([1,2,'a','b']) == [1,2]
  filter_list([1,'a','b',0,15]) == [1,0,15]
  filter_list([1,2,'aasf','1','123',123]) == [1,2,123]
  ```

  :arrow_right:  My solution: 

  - Using ".map" method to solve this problem

  ```ruby
  def filter_list(l)
    return l.select{|item| item.is_a? Numeric}
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def filter_list(l)
    l.reject { |x| x.is_a? String }
  end
  ```


### 9.  Credit card mark (7kyu)

  :bell:  Task: [Credit card mark](https://www.codewars.com/kata/53dbd5315a3c69eed20002dd)

  >Usually when you buy something, you're asked whether your credit card number, phone number or answer to your most secret question is still correct. However, since someone could look over your shoulder, you don't want that shown on your screen. Instead, we mask it. Your task is to write a function maskify, which changes all but the last four characters into '#'.

  >For example

  ```
  maskify('4556364607935616') # should return '############5616'
  maskify('64607935616')      # should return '#######5616'
  maskify('1')                # should return '1'
  maskify('')                 # should return ''

  # "What was the name of your first pet?"
  maskify('Skippy')                                   # should return '##ippy'
  maskify('Nananananananananananananananana Batman!') # should return '####################################man!'

  ```

  :arrow_right:  My solution: 

  - I keep only 4 last caracters of string, and add the "#" (string.length-4) times in the first.

  ```ruby
  def maskify(cc)
    return cc.length <= 4 ? cc : ('#' * (cc.length-4)) + cc[cc.length-4..cc.length-1]
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def maskify(cc)
     cc.gsub(/.(?=....)/, '#')
  end
  ```
  ```ruby
  def maskify(cc)
    cc.size <= 4 ? cc : "#" * (cc.length-4) + cc[-4..-1]
  end
  ```
  Very easy to read the code with the best solutions on codewars.

### 10. Categorize new member (7kyu)

  :bell:  Task: [Categorize new member](https://www.codewars.com/kata/53dbd5315a3c69eed20002dd)

  >The Western Suburbs Croquet Club has two categories of membership, Senior and Open. They would like your help with an application form that will tell prospective members which category they will be placed.

  >To be a senior, a member must be at least 55 years old and have a handicap greater than 7. In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.

  >Example input

  ```
  [[18, 20],[45, 2],[61, 12],[37, 6],[21, 21],[78, 9]]
  ```
  >Example output

  ```
  ["Open", "Open", "Senior", "Open", "Open", "Senior"]
  ```

  :arrow_right:  My solution: 

  - The method ".map" is again take the job done

  ```ruby
  def open_or_senior(data)
    return data.map{|person| (person[0]>=55 && person[1]>7) ? "Senior": "Open"}
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def openOrSenior1(data)
    data.map { |age, handicap| age >= 55 && handicap > 7 ? "Senior" : "Open" }
  end
  ```

### 11. Find The Parity Outlier (6kyu)

  For the last challenge, i will take an kata of 6kyu.
  It will be a little more complex of the previous challenges.

  :bell:  Task: [Find The Parity Outlier](https://www.codewars.com/kata/5526fc09a1bbd946250002dc)

  >You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N..

  >For example
  ```
  [2, 4, 0, 100, 4, 11, 2602, 36]
  Should return: 11 (the only odd number)

  [160, 3, 1719, 19, 11, 13, -21]
  Should return: 160 (the only even number)

  ```

  :arrow_right:  My solution: 

  - Because our array contains an unique even number or odd number. So I will check 3 first items in array. If it contains 2 and more even number, so the number that we need to find is a odd number, and vice versa.
  - After checking, we can easily find the result with the method ".select"

  ```ruby
  def maskify(cc)
    is_all_even = integers[0..2].select{|x| x%2 ==0}.size > 1
    return is_all_even ? integers.select{|x| x%2 != 0}[0] : integers.select{|x| x%2 == 0}[0]
  end
  ```
  :heavy_check_mark: Best solution on codewars

  ```ruby
  def find_outlier(integers)
    integers.partition(&:odd?).find(&:one?).first
  end
  ```
  ```ruby
  def find_outlier(integers)
    outlier = integers.first(3).count(&:even?) < 2 ? :even? : :odd?
    integers.find(&outlier)
  end
  ```
  Thanks to the developers on the codewars, I could learn about the "partition" method. That return two arrays by the given condition. I could not never know this method if I just learn on the basic document. 

## Reference

You can find the code in my github repository <i class="fab fa-github"></i> [Codeward Ruby](https://github.com/tienduy-nguyen/coding-challenge/tree/master/codewars-ruby)

The Hacking Project website [thehackingproject.org](https://www.thehackingproject.org/)

Codeware website [coderwars.com](https://codewars.com)

## Series Ruby Coding Challenges

1. [Ruby Coding Challenges with TheHackingProject - 01](/coding-challenges/ruby-codling-challenges-with-the-hacking-project-01)
2. [Ruby Coding Challenges with TheHackingProject - 02](/coding-challenges/ruby-codling-challenges-with-the-hacking-project-02)
3. [Ruby Coding Challenges with TheHackingProject - 03](/coding-challenges/ruby-codling-challenges-with-the-hacking-project-03)


**I hope you like this serie. The next challenges will be so much more instesting of this serie. Follow me to get the new update.**

{% include eof.md %}