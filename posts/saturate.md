---
title: saturate.txt
date: 2020-06-05
tags: dev
layout: layouts/post.njk
---

start with something basic, and then saturate the space of possibilities.

for example: name/value pairs.

say the name is a string (utf?).
the value can be ... anything?
the value has a type.

so in the system (firkin, for now)
we write functions which assign values
to names, triggered by other values
changing

```
x, y -> z
{
	z = x*x + y*y
}
```

so we can already show that there are several
possibilities for how the system might work.

1. can't change type

so how is the type of these values determined?
(important, perhaps fundamental, is the fact
that we are no longer assigning types to
input/output - rather we are assigning names!

the other important point has to do with reactivity,
though i've yet to clarify for myself what that
really means...)

What are some options?

a) Types are declared up front for some reason

(remember, we define a global namespace, literally -
a set (list) of names, each with a value).

b) The types are determined by the function.

You could type them, though they so have types
at all times - perhaps including 'undefined'.

(Also important is that this whole thing will look
different, and even differently with-in, each
programming language it is implemented in.
It is not necessarily just tied to one language.
Or even it's own language... though that is
an interesting idea too, having it's own language...)

Quite interesting - redis is a name/value pair
database, but each value has a type:
Strings, Lists, Sets, Sorted Sets, Hashes, HyperLogLogs, Bitmaps.

Another interesting idea: you can use naming
convensions for classes in a string:

`@myclass/member_variable` ....

then you just add the list of connections as functions

```
[store].add_fn([@myclass/member_variable, fn, @myclass/output])
```
And then I suppose you could limit the outputs of some functions
to not be in the global 'space' ???

