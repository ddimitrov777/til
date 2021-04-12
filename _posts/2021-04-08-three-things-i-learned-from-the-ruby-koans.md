---
layout: post
title: Three things I learned from The Ruby Koans
---

Here are (at least) three things I learned from [The Ruby Koans](http://rubykoans.com/):

* Case syntax for Ruby, so I can replace nested ifs. (Learned this in the triangle exercise)
~~~~
case [a,b,c].uniq.size
when 1 then :equilateral
when 2 then :isosceles
else        :scalene
end
~~~~
Instead of:

~~~~
def triangle(a, b, c)
  if ((a == b) && (a == c) && (b == c))
    return :equilateral
  elsif ((a == b) || (a == c) || (b == c))
    return :isosceles
  else
    return :scalene
  end
end
~~~~
* Exceptions fit into the Object hierarchy, such as in this example: RuntimeError < StandardError < Exception < Objection
* Begin rescue ensure end.... Rescue from an error exception... Ensure a code happenps no matter what
* .each is a prebuilt method in the Array class
* The use of blocks
e.g. two ways to do the same thing

~~~~
array.each do |item|
   sum += item
end 
~~~~

Vs

~~~~
array.each { |item| sum += item }
~~~~

