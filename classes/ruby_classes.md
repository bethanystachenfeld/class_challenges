
# Ruby Classes

Let's start by creating a class:

```ruby
class Person

end
```
Pretty simple stuff right?<br>

As you've heard many times before. In Ruby _everything is an object_... The job of a class is to define all of the logic and actions that will be available to our object. 
<br>

In order to **instantiate** (create) objects of a **class**, your class must include an initialize method


**Challenge 1 (part 1)** 

1. Create a Person class
2. Add an initialize method
	3. include the paramaters
		- first_name
		- last_name
		- occupation 
<br>

The initialize method runs when you **create** an object (get it? **initialize**).
<br> 
Now, you'll need to turn those *parameters* into *arguments* and make them available throughout the class
<br>

**Challenge 1 (part 2)**

Take the attributes (first\_name, last\_name, and occupation) 
<br>

1. turn them into variables
2. make those variables available througout the class.


*hint: Think about scope and local variables. How do other methods get access to variables stored within this method?*

- - - -
##Instantiation

***Instantation*** - the 'computer-sciencey' way of saying "Let's create an object"

Now that we have an *intialize method* we can create an _instance_ (object) of the Person class.
<br> 

`good_guy = Person.new("jim", "gordon", "detective")`

When the code above runs, here is what happens: 

1. Person.new calls the initialize method
2. which in turn looks for the following paramaters 
	3. first\_name
	4. last\_name
	5. occupation
6. It then takes those paramaters and assigns them to instance variables (so we can have access to them)
7. We then assign the new **object** to the good_guy variable. 
8. So, good_guy is reflecting the *state* of this specific object.

Try printing good\_guy to the screen `puts good_guy` 
<br>
Run the program...

You'll probably notice that you get a return value similar to this:
`#<Person:0x007f84aa1af140>`

So, that's great. but what does it mean?
<br>
In a nutshell, this is showing us that good\_guy belongs to the Person class... and all the numbers are the location of this object in memory. 

Try this:
 print good\_guy to the screen 2 or 3 times and re-run the script several times.
 
 ```ruby
 puts good_guy
 puts good_guy
 puts good_guy
 ```
 
 You'll see that the numbers after `#<Person:` change each time, but they are the same on all 3 lines


```
#<Person:0x007fd83b866788>
#<Person:0x007fd83b866788>
#<Person:0x007fd83b866788>
```

- - - -
##Getters and Setters

So, cool... we can see our object is being created, which is great. But getting back this blob of information isn't really going to be useful to an end-user of our program.

How do we get access to the first_name?

This should be as simple as calling `puts good_guy.first_name` right?
<br>
Try it...
Change the last line of your program and run the script.
<br>

Well... that sucks. you probably got an output like this:

```
#<Person:0x007ff849912898>
#<Person:0x007ff849912898>
people.rb:14:in `<main>': undefined method `first_name' for #<Person:0x007ff849912898> (NoMethodError)
```

Let's break this down <br>

The error message is trying to help us by saying that **first_name** is an undefined method on the object. 
So... how do we fix it?

We could try creating a method. 
 
 **Challenge 2**

1. Create a first_name method 
2. Call the method and make it print to the screen.
 


Okay, so what's happening here? 
We are creating an ***instance method*** that gives us access to the @first_name variable. 
<br>
Now when we call `puts good_guy.first_name` we'll get back the following:

```
#<Person:0x007fde73a4f408>
#<Person:0x007fde73a4f408>
jim
```

This type of method is referred to as a **getter**. That's right, it allows for us to access the object's attribute. (in this case, the attribute is first_name).
<br>


That's great! But what if we want to update the object's first_name attribute?
<br>
We could try this:

```ruby
good_guy.first_name = "james"
puts good_guy.first_name 
```

However, that will produce another error:

```
#<Person:0x007f82721ae860>
#<Person:0x007f82721ae860>
jim
people.rb:23:in `<main>': undefined method `first_name=' for #<Person:0x007f82721ae860> (NoMethodError)
```
Ah! another **NoMethodError**, By now, I'm sure you're thinking "Oh! we just need another method!"
<br>
...And you'd be right! we need a **setter** method...
<br> Here's how you do it:

```ruby
 # setter method in ruby
  def first_name=(new_name)
    @first_name = new_name
  end
```
So, what's happening here is pretty simple. (Don't let the = sign throw you off). Because we want to redifine the @first\_name attribute, we'll need to pass a new\_name argument. Then, we take that new_name parameter, turn it into an argument and assign the new value to the @first\_name instance variable.

try running this now:

```ruby
good_guy = Person.new("jim", "gordon", "detective")

puts good_guy
puts good_guy
puts good_guy.first_name
good_guy.first_name = "james"
puts good_guy.first_name
```
You should get the following:

```
#<Person:0x007fe0340fe440>
#<Person:0x007fe0340fe440>
jim
james
```

Awesome! you've just created getter and setter instance methods!

**Challenge 3**

- Write the getter and setter methods for the last_name and occupation attributes.

- - - -
## Answers

####Challenge 1
```ruby
#(part 1)
class Person
	def initlialize(first_name, last_name, occupation)
	
	end
end
```	
```ruby
# (part 2)
def initialize(first_name, last_name, occupation)
	@first_name = first_name
	@last_name = last_name
	@occupation = occupation
end
```

####Challenge 2
```ruby
def first_name
	@first_name
end
```
  
####Challenge 3
```ruby
def last_name
	@last_name
end

def last_name=(new_name)
	@last_name = new_name
end

def occupation
	@occupation
end

def occupation=(new_occupation)
	@occupation = new_occupation
end  
```













