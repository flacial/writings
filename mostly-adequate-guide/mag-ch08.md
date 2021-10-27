**Chapter 08: Tupperware (Functors)**

Functor: a type that store a single or multiple values and implements map
	- A value in a Functor stays in it.
	- - A valid functor has to satisfy identity and composition law.
	- **The 3 types of the introduced functors**
		- Maybe: used when a value might not exist. It's also an object that help us to add safety to our functions
		- Either: used for error-handling with `left`
		- IO: used for keeping side-effects under control by delaying their execution
		- Task: used for asynchronous tasks
		- IO and Task are like guns. We keep filling them with bullets, and when the time is right, the trigger is pulled (release the functor's value).
	- **Lifting:** the transformation of a function that doesn't work on functors (non-functory) to functory one that does by using `map` .
  
Thoughts:
	- The reason behind creating a new Functor each time the functor's value is manipulated is because one of FP pillars is immutability.
	- The point of FP isn't to eliminate side-effects, but to manage and control them.