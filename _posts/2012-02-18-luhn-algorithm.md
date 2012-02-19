---
layout: post
title: Luhn Algorithm
---

[wiki]: http://en.wikipedia.org/wiki/Luhn "Wikipedia: Luhn Algorithm"

Problem
-------
The Luhn algorithm, also known as the "mod 10" algorithm (see
[Wikipedia] [wiki]), is a simple checksum formula used to validate
a variety of identification numbers. Given a numeric input, the
algorithm works as follows:

  1. Counting from the check digit, which is the rightmost, and moving left,
     double the value of every second digit.

  2. Sum the digits of the products (e.g., `10 = 1 + 0 = 1, 14 = 1 + 4 = 5` )
     together with the undoubled digits from the original number.

  3. If the total modulo 10 is equal to 0 (if the total ends in zero) then the
     number is valid according to the Luhn formula; else it is not valid.

Example
-------
{% highlight ruby linenos %}
  luhn?('42')   => true    # 2 + 8 = 10
  luhn?('9001') => true    # 1 + 0 + 0 + (1 + 8) = 10
  luhn?('43')   => false   # 3 + 8 = 11
  luhn?('0175') => false   # 5 + (1 + 4) + 1 + 0 = 11
{% endhighlight %}

Solution
--------
{% highlight ruby linenos %}
  class CreditCard
    def self.luhn?(number)
      num_a  = number.reverse.split('').map { |n| n.to_i }
      sum_a  = [0, 2, 4, 6, 8, 1, 3, 5, 7, 9]
      result = 0

      num_a.each_with_index do |num, i|
        result += i % 2 == 0 ? num : sum_a[num]
      end

      result % 10 == 0
    end
  end
{% endhighlight %}
