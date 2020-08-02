---
title: confidence and software.txt
date: 2020-06-16
tags:
layout: layouts/post.njk
---

i think perhaps my relationship with software has been a
personal search for confidence.

how does one get confidence? take a look at this code:

```c
int add_one( int n )
{
	return n + 1;
}
```

the first line tells me that i know this function will
produce an integer because it has been _enforced_ by
the language. i can be confident of this. it is, in this
context, a *fact*. also, because the language will
ensure the value coming in is an integer, and because
in `c` adding two things with a plus sign, and integers,
adds two integers together (i.e. not overloaded),
we can safely assume that this function will in fact
return the number plus one....
(actually we can't!.... but let's ignore this for now...)

what about the opposite: when is one not confident?
a lack of confidence comes when one does not know
what will happen:

```c
int add_external( int n )
{
	return n + rnd_fnc();
}
```

confidence is a crap thing to talk about.
most people, most men in my estimation, don't like to do
it. but in my work i hit the same issue over and over
(and over) again - i lack confidence in my code.
and it's not emotional, i'm not insecure. i just don't
know what my code is doing, whether it will work in all
the necessary circumstances. and i'm starting to feel
as though this is a problem that can be solved in the
abstract: that there are principals one could develop
to mitigate this.

of course, this is what has been obsessed over for
millenia. the foundations of logic, mathematics, programming.
it goes on and on and every day new products and packages
and libraries are being released, written about, debated,
tinkered with, invented. but i feel like i am personally
on the verge of simplifying all of it to an idea, or
a direction. it's not about a library or a language - 
those can be designed to align better to this fact
but any library or language can be used badly, by nature
of it's intended generality. and i'm not talking about
a mathematical proof, either - i spent years studying
mathematical concepts at university and left
dissilusioned at how little importance or connection
they had to the problems people faced trying to build
things in the world. though of course some of the more
basic tools of mathematics can be used to great effect in
proving assertions in coding. i'm thinking of sql.

no, what i want to discuss is code. i want to have an
honest discussion over what it's like building computing
systems for a living. and why it is that every project
ends up with run away complexity. perhaps there is a group
of people somewhere who manage to design and develop
systems that are robust and predictable and maintainable
and extendable and they can all sleep at night because
they know like they know `2+2=4` that everything will
work as intended, and if they are then i'm not hearing
from them in blog posts, and i'm not reading the books
they've written, because i read voraciously and have
done so for over 20 years on this topic and i haven't
found anyone who just says "if you do this then you
will be able to manage what you create".

and i feel as though it all can be built around one
idea, one word: confidence. one lacks sleep because
of lack of confidence. one struggles to maintain a
software project because of lack of confidence (not
the emotional kind, the other kind). one struggled to
extend a software project because of lack of confidence
(again, not the emotional type. though i'm beginning
to wonder if they are connected). one becomes stressed
out working as a programmer in my experience because
of lack of confidence: not because you aren't gung-ho,
but because you have integrity and you know deep down
that things aren't certain. and my question is why:
why are you not confidence (in the code!) ? it's not
about warm guey feelings, you don't need a hug. if we
could just figure this out, if there was a way of taking
this virtually deterministic thing that we have near
complete control over and corrale it in the right
way, with wisdom, we could get there: we could build
confidence from the ground up. and maybe then even
progress with the emotional stuff too. i feel like if
we just had an honest discussion about this, about
confidence being the root of our problems, then we
could start to think about and lay out where we see
confidence and where we don't, and then start to
discover what underlies it and what we can do about
it.