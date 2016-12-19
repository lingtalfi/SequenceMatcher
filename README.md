SequenceMatcher
=========================
2016-12-15


Find/replace a pattern in a sequence of things.



Sometimes, you have a sequence of things and you need to find a pattern of those things in the sequence.

If those things were characters, then the sequence of things would be a string, and you could use the php regex functions.

Regex only applies to strings though, so what if you need to parse a more abstract sequence of things?

That's when the SequenceMatcher can become handy.

Although it doesn't have all the bells and whistles of the regex, it has two or three useful features that allow
basic searching through a sequence of things.

In other words, the SequenceMatcher is an simplified abstraction of the regex engine, which works with things, not only
characters.





Concepts
-------------


A sequence contains an arbitrary number of things.

A thing can be anything: a number, a character, an array, an object, ...

When you want to match a particular combination of things in the sequence, you first create what's called a model.

A model is like a pattern in the regex model: it's basically a blue print used to match against the things in the sequence.

A model is composed of elements.

There are three types of elements:

- entity
- group (of elements)
- alternate (group of elements)


The entity is the smallest and most fundamental element.

It's an intelligent object which has a match method (i.e. it is able to tell whether or not it matches
against a given thing).



The group and alternate group are syntactic element.

The group is a container for other elements,

and the alternate group allows the parallelization of groups (useful in some cases
where you want to match one of different alternatives).



The model is then given to the SequenceMatcher.

The SequenceMatcher can only work with one model and one sequence at the time.

The SequenceMatcher parses the sequence of things, and, using the different elements, finds whether or not the model
matches the sequence of things.

The model may be found zero, one or more times.


You can add listeners to the SequenceMatcher, in order to do something useful when a match is found.

There are two main things you can do:

- accessing the matched entities; this is useful if you want to extract some information out of a sequence (think preg_match)
- replace the matched entities by a subsequence of your choice (think preg_replace)




Modificators
----------------------

Beside the elements, the SequenceMatcher also provides the following modificators (inspired by regex):

- ? modificator
- + modificator
- * modificator



Modificators can be applied to all elements.




Some notes about the implementation
-----------------------------------

An element has a __toString method, because it eases the testing phase (and coding this object was hard for me...).

I have to say, the implementation is quite weak: and since I was not confident in
the code, I compensated with some tests.

Basically, I built up the tool until I could use it, but it might not work
for your cases.

The way it's implemented, I believe the best way to extend it is to
read the tests and use the "test first" method (writing your tests before you
implement a new functionality or when you find a bug).

The tests are in the btests directory of this repository.

Good luck.


























