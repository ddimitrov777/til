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
e.g. two ways to do the same thing... the {*some stuff*} is essentially synonymous with a **do** *some stuff* **end** encapuslation

~~~~
array.each do |item|
   sum += item
end 
~~~~

Vs

~~~~
array.each { |item| sum += item }
~~~~

* Instead of .each, we can use other methods... like .collect or .map
  * .collect / .map transforms the elements in the array
~~~~
array = [1, 2, 3]
    new_array = array.collect { |item| item + 10 }
    assert_equal [11, 12, 13], new_array
~~~~ 

* We can also use .select /.find_all procedure
e.g. if we want to select all even numbers from within an array:

~~~~
array = [1, 2, 3, 4, 5, 6]
even_numbers = array.select { |item| (item % 2) == 0 }

#even_numbers now returns [2, 4, 6]

~~~~
* In this vein, .find will return the first matching instance
*  .inject/.reduce method... what you put in the paranthesis is the starting value for the sum/product/etc. These methods allow you to do a sequential procedure where you start with the first item, relate it to the second item (typically aggregating them in some way)... take this new combination/aggregation and relate it to the next item in the list... etc.

Another way of saying it... there are two terms in an .inject method. The first is an accumulator term, the second is the current element.

A creative way to use .inject could be to build a hash
~~~~

[[:student, "Terrance Koar"], [:course, "Web Dev"]].inject({}) do |result, element| 
    result[element.first] = element.last 
    result
end
#=> {:student=>"Terrance Koar", :course=>"Web Dev"}

~~~~

(you could also change the datatype and do other operations in there, such as having element.first.to_s in the above example)

* The ampersand (&) sign can be used as syntactic sugar for blocks

~~~~
method { |param| param.some_method }
~~~~

can be written as

~~~~
method &.some_method
~~~~

or

~~~~
method(&.some_method)
~~~~



* There are some more block arguments and methods to go back to... e.g. using yield, lambda, .call, et
* There is an instance_variables method to fetch instance variables associated with the class you've specified.
* Instead of calling a method name by .method_name, you could also use the .send(:method_name) syntax, which allows dynamic changing of method names
* def end encapsulations can be thought of as funcitons you can call or purely as code dividers to delineate different sections
* Use def **initialize**(arg1, arg2) to create Objects that require arguments... 
e.g. like if you have a point object


~~~~
class Point
  def initialize(x, y)
  end
end

#In this example, you may want to store the arguments into instance variables
~~~~

* A class is like a category of being… it doesn’t become an object until you have .new 
You make a new object from the category of being
Class is blueprint, object is product

* Alternative array notation of  **%w()**
%w(foo bar) is the same as [“foo”, “bar”]
semantically remember that it's a White space separated array

* **super** calls a parent method with the same name
