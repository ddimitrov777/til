---
layout: post
title: Three things I learned from The Ruby Koans
---

Here are (at least) three things I learned from [The Ruby Koans](http://rubykoans.com/):

* case statement as an option for the triangle condition
~~~~
case [a,b,c].uniq.size
when 1 then :equilateral
when 2 then :isosceles
else        :scalene
end

###INSTEAD OF:

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
* 
