---
layout: post
title: Things I learned from Week 2
---

# Exercism

* Ruby each_slice enumerable method (to split array into arrays)
* .each_line, split string that has multiple line into array of stirngs separated by lines (and then you can enumerate
```
#different options

"hello\nworld".each_split{|s| p s}
"hello\nworld".each_split(chomp: true) {|s| p s}
```
* Enumerators
We call an object “enumerable” when it describes a set of items and a method to loop over each of them

Enumeration traverses over objects
If you supply an enumerable (like an .each) without a subsequent block, then you get the Enumerator Object... You can assign that object to a variable and then do somethings with that Object.
e.g.

```
enum = "hello".each_char
enum.map &:upcase

# ==>.  ["H","E","L","L",O"]


```

* How to make attr_reader and accessor work with question mark methods?
Use alias_method
```
attr_reader :server_error
alias_method :server_error?, :server_error
```


* From isogram… Approach for string functions… eliminate excess/non-useful variation… we do downcase since we don’t care about case (to standardize and eliminate case variation)… 
* .chars splits a string into an array of chars
* Array subtraction to eliminate any copies of a value from the original array
[1,2,3,4,5] - [1,3,4]  #=> [2,5]
This works with duplicates
[ 1, 1, 2, 2, 3, 3, 4, 5 ] - [ 1, 2, 4 ]  #=>  [ 3, 3, 5 ]
Useful for strings
To eliminate any spaces or other undesirable characters
word.downcase.chars - [' ', '-']
* Let’s generalize this as its own bullet point… to eliminate undesirable characters from string, convert to array of characters and subtract out the undesirables
* .tap method to 1) streamline code 2) for debugging

1)
user = User.new.tap do |u|
  u.build_profile
  u.process_credit_card
  u.ship_out_item
  u.send_email_confirmation
  u.blahblahyougetmypoint
end


2)
(1..10).map {|x| x*x }.tap {|x| puts "array: #{x.length} items long"}.join

array: 10 items long
 => "149162536496481100"

Here’s another example of .tap where you can use it to exit a method that has a chain

.tap { |s| return false unless s[/\A\d\d+\z/] }

* Delete spaces with .gsub(/\s/, ‘’)


* If else ternary operators
Substitute

If condition
some_stuff
else
other_stuff
End

With

condition ? some_stuff : other_stuff

￼

You can even put the condition in a variable

* If you declare an instance variable in one method within a class and need to use it in another method… call the method 1

￼
^@numcols was first declared in 
def rows

* Instance variables are applied to each class Object… say you have a CoffeeMachine class with a water level instance variable, @water . … if I have 10 different coffee machines, they will each have a different water level… so the @water for coffee machine #1 will be different than the @water for CoffeeMachine #2

* Method arguments… 
def method(argument) 
end

#multiple arguments
def method(argument1, argument2, argument3) end

#optional argument (you need to specify default)

def method(argument1, argument2 =“default value”)     #==>makes argument2 optional
end

#variable arguments (allowing you take unlimited amount of values)
def method(*args)
end

#having some variable options
def print_all(title, *chapters)
end

#keyword arguments (optional for readability)

￼

#valid order of arguments if you want to incorporate multiple types
required -> optional -> variable -> keyword




