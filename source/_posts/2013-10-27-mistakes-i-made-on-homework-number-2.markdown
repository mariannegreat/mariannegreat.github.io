---
layout: post
title: "Mistakes I made on Homework #2"
date: 2013-10-27 17:57
comments: true
categories: 
---
In solving homework #2, I had to understand *attr_accessor*. (Side note: I'm slowly learning that a "method" is essentially a function -- a weird piece of terminology that I haven't been able to get used to, for some reason.)

In the future, I think I'll start taking screenshots of my in-progress, error-prone code as I do my homework. For now, here's some things that I struggled with but figured out while solving last week's Homework #2. 

An errant code sample: 

	class Story
	  	attr_accessor :title
	  	attr_accessor :category
	
		def initialize title, category 
			@title = title
			@category = category
		end
		
		def upvotes
			1
		end
		
		def upvote
			upvotes = upvotes + 1
		end
		
		def downvote
			upvotes = upvotes - 1
		end
	end
	
After setting *story = Story.new*, *story.upvotes* DID return a value of 1. But I didn't make *upvotes* writable… whoops. 

I guess I thought that *upvote* and *downvote* would be able to access the *upvotes* method to return the right values.

So… the key to figuring out the problem was to make @upvotes a variable! Duh.

	attr_accessor :upvotes
	
*attr_accessor* essentially creates a method called *upvotes* that returns the value of a variable *upvotes* (reader), and a method *upvotes=* that allowed the variable *upvotes* to be rewritten (writer).  

According to the requirements of the homework, *upvotes* needed to be set at a value of 1 upon initialization. To be honest, I don't know if the placement of attr_accessor above or below the initialize method makes a difference. But it did need to be set as 1, so I put that in the initialize function: 

	def initialize title, category 
	  @title = title
	  @category = category
	  @upvotes = 1
	end
	
Of course, it doesn't need to be set as an argument since the user is not defining it. 

From there it was a simple matter of creating the *upvote* and *downvote* methods. (Ugh, I always want to say "function" -- I'm gonna need to get used to that.)