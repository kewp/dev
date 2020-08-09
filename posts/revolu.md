---
title: revolu.txt
date: 2020-06-06
tags: dev
layout: layouts/post.njk
---

i think i may have stumbled onto a new approach to programming
that may just be revolutionary.

I plan to write about the _history_ of the idea and
to publish various _exploratory toys_
but here i want to jump straight into the implementation
and flesh out the philsophical implications.

suppose you have a list of structures, each of which is
made of two lists of strings and a function.
Here I'll use the JSON convention to indicate
lists `[]` and objects `{}`.

```json
[
    [
        ['one', 'two'],
        ['three', 'four'],
        fn_a
    ],
    [
        ['right', 'left'], 
        ['distance'],
        fn_b
    ],
    [
        ['x', 'y'],
        ['z'],
        fn_c
    ]
]
```

Let us now say that each of these sub-structures,
let's call them _tenets_,
define three things: a list of inputs, a list of
outputs, and something that takes the inputs to
produce the outputs, i.e.

```
inputs -> fn -> outputs
```

So essentially we've describes a set of rules,
without saying anything of the implementation,
of how a set of values (just names, no types)
are produced with relation to others.

Let me pause here to encapsulate this. The structure
above is the complete extent of what I'm suggesting
is so revolutionary. It may not look like much but
I have reason to believe it has profound implications
for software development, from usability, robustness,
execution - essentially I feel this is how all software
should be written fundamentally. But it will take
some doing laying out everything I have in my head
about why that is, let alone knowing how to order it all.
Perhaps in the process I will
realise my vision doesn't make sense. Let's continue.

We can say a lot already simply by the structure above
and it's meaning - two lists of names as input/output
and a function connecting the two. What can we say about
it? Let's look at an example.

Suppose I have this list (I'm going to try use a less
obtuse format)

```
1. x -> y
2. x, y -> r
```

(It will strike many that this looks like functional
programming which I will discuss soon. I think there is
a critical difference).

We have two sets of relationships - instead of showing
a function name i've numbered them. Hopefully it's clear
that this is equivalent to say, for example,
`{['x'], ['y'], fn_one}`.

Let's define these functions.

```js
fn_one = (x) -> 2*x + 1
fn_two = (x,y) -> x*x + y*y
```

We could write this is old Javascript like this

```js
function fn_one (x) { return 2*x + 1; }
function fn_two (x,y) { return x*x + y*y; }
```

(Essentially (1) describes a linear graph and (2)
gives the distance to the origin, squared).

Now let's make a statement, an assignment if you will:

```js
let x = 5
```

What does this mean? Bare with my if this seems tedious.
Since we know `x` we can get `y` from (1).
Now since we know `x` and `y` we can get `r` from (2).

## Observation 1

How is this any different from ordinary software / function
writing? Well as you can see, we do define the functions
as per normal software. The difference is that here
we are making _declarative_ statements about connections
between values.

The set of functions above

```js
function fn_one (x) { return 2*x + 1; }
function fn_two (x,y) { return x*x + y*y; }
```

say nothing about how these functions connect,
or in fact what they are outputting (in terms
of names).

Ok, how would we write the same "program" as the
one we defined above?

```js
function main()
{
    let x = 5;
    let y = fn_one (x);
    let r = fn_two (x,y);
}
```

Right, so this function (`main`) connects these
values, and using variable names it gives us a
sense of what they mean. This is how software
is written these days.

But take a look at this:

```js
function broom()
{
    let couch = 5;
    let brown = fn_one (couch);
    let mouse = fn_two (couch, brown);
}
```

The way we have write functions today are
as these generic processors - something
reusable. As such the names don't matter,
only the types.

To illustrate, take a look at this:

```js
function green (x) { return fn_one(x); }
function blue (a,b) { return green (x) * fn_two(a,b); }
function main()
{
    let x = 5;
    let y = green(x);
    let r = blue(x,y);
}
```

(I feel like I've already made a strong point
just with this, though it's super vague and
probably just personal, but just look at that
code: all meaning has been lost. Not only
that, already I can't figure out what it is,
I mean it's geometry...).

Let's jump back to the original structure
and look at how it's different.

```js
let tenets = [
{
    ['x'], // inputs
    ['y'], // outputs
    fn_one
},
{
    ['x','y'],
    ['r'],
    fn_two
}
]

function fn_one (x) { return ... }
function fn_two (y) { retrun ... }

function main()
{
    set(tenets, 'x', 5);

    let r = get(tenets, 'r');
}
```

Here I've written out an almost working
Javascript implementation - we just need
to define `get` and `set`.

As you can see, you never use functions
inside of your 'program' (here just `main`).
Rather all you do is set variable values.

-----

tag line:

firkin is a simple but new approach to 
writing software that upends the industry,
producing systems that are:

- provably robust
- reproducable (and thus trivially testable)
- understandable (!)

the idea is both easy to understand
and to implement, though once understood
it's hard to see how the above properties
arise from it. let's start with describing
the idea, then doing a short implementation,
and finally trying to illustrate why
software systems produced in this way
would have such a profound advantage over
any other system we have so far.

1. the idea

in plain english: you have an object you
use to get and set values; height, person,
record, distance; but in addition add
relationships between values. that's it.
end description.

let's walk through it again.

object
 - value
 - value
 - value
 - relationship
 - relationship
 - relationship

 an object has a list of values
 and a list of relationships.

let's take a more specific example.

person
 - height
 - weight
 - bmi
 - height, weight -> bmi

body mass index is calculated as
weight / height^2 (or something).
so a relationship is just values
in and values out.

[value, value, value] -> relationship -> [value, value, value]

now we need to talk about programmers:
an ordinary person would look at this
and think it was pointless. a programmer
would say "this looks like classes - you
have members and you have functions".

the first point is right - we have members:
a string 'name' and a value, which has a type.
but a relationship here is not a function.
crucially, it's a definition. it says
"you produce these values with these"
and the definition of the function
uses _names_ not _types_.

1.1 names not types

this is what a function in programming
looks like

```js
int total (double a, int b)
{
    return a + b;
}
```

the function has a name - a string of
letters, say. the function also has
a type, which specifies the type
of the return value (here just one
value). also it has a list of inputs
which have both a name and a type.

what i'm suggesting is this:
orchestrating logic with types is bad.

consider unix pipes. widely lauded for
it's design robustness, it operates
under a single paradyme: the text
stream. does a text stream have a type?

software is written with functions
which really are _utilities_. they
are tools you can use to make complex
things. but there is a fundamental
aspect of writing software that has
not been well understood, and which
has led to hitting hard limits
to complexity: orchestration. every
software project i've ever worked
on has required total dedication by
some unlucky fool to keep the entire
ediface of the the tower of babel
in their minds. even a few months
lapse renders them useless, let alone
anyone else who would have to look
at it. why? what makes software so
fundamentally complex? we are missing
the point.

consider the situation above:
we have a formula to calculate the
body mass index based on weight
and mass. here is how we would
implement this using software today:

```c
float bmi (float m, float h)
{
    return m / (h*h);
}

int main()
{
    float mass = 75.0; // kgs
    float height = 1.85; // meters
    float bmi = bmi (mass, height);

    printf("bmi = %.2f\n", bmi);
}
```

 - we put our values, mass and height, into two variables
 - we "pass" those variables to a function, which returns a value
 - we save that value into a variable called _bmi_ by virtue of the equal sign

what's wrong with this? well, you
have put the orchestration into the
hands of the programmer - anyone with
a keyboard and a c compiler can use
your function to their own nefarious
ends.

```c
int main()
{
    float x = 1.23;
    float y = 3.23;
    float distance = bmi (x, y); // technically correct!
}
```

again, all a function does is say
"take these types, _in this order_,
and produce this type". what says *nothing*
of the operation of the function or
the context!

imagine instead the function looked like
this:

```
mass, height -> mass / (height*height) -> bmi
```

some would think this is like functional
programming but it's not - this is not
a declaration of a type signature.
in fact there's several things different:

- you have to use the same names
- the inputs and outputs exist on the same scope
- you don't decide when to 'execute' this relationship or make it happen

so you never say "go ahead and put this value into bmi".
rather you say beforehand "the value bmi is _always_
equal to mass / (height*height)" and then
bmi is updating by another mechanism, outside the
programmers concerns.

