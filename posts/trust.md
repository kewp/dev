---
title: trust.txt
date: 2020-11-04
tags: dev
layout: layouts/post.njk
---

i think i've come upon a way of looking at writing code that explains
what makes it easy and hard to use, what makes it _good_ or _bad_,
what makes it hard to maintain or not. what makes it robust or buggy.

from the title you can see it's something about the word **trust** and it literally
is trust. but there is a ton to unpack.

the first thing, though, is about me and you, the reader. do you trust me?
right now you're trying to figure out how to feel about what i'm writing.
i've just said i have something important to say about programming, that
i've come upon this brilliant thing that will transform your work and your
life. should you trust me? should you even keep reading? who am i, how
do you determine that i am someone you should be listening to?

it's a long, complex topic - all of programming. it might take a long time
to upend all of it, it might take a lot of thought and consideration and
patience to really fundamentally shift the way you see it. that's a huge
investment, so who am i to do this - you only have so much time. if you spent
it all thinking about every opinion someone claims is important you would
get lost quickly.

people have also been trying to
make programming better for decades. and i'm sure you have used it yourself,
perhaps for years. you've already read so many different opinions, and anyone
who has programmed has spent so many hours thinking themselves of how it
might be better.

so here already this notion is trust shows it's importance. and as always,
when i really come onto an idea i think is profound about programming it
seems to leak into the outside world. but programming is such an interesting
petri dish because we can analyse it without getting mired in debates about
meaning.

this post was largely inspired by an article by the guy who wrote PureScript
https://www.reaktor.com/blog/fear-trust-and-javascript/
though it's incredible close to many things i've been wondering about.
he lays it out very clearly - that what we want when we are writing
functions is trust. i am going to try expand it to _all_ of programming
is about trust. and perhaps also connect it to trust in, well, all of life.

----

well let's start with _all of life_ since it's such a hokey thing to say.
what problems do you have?

 - money
 - relationships
 - crime
 - loneliness
 - globilization
 - meaning

it's pretty easy to see how each can be related to the idea of trust.

 - _money_ will i have enough money in the future?
 - _relationships_ will this person hurt me?
 - _crime_ will i be safe?
 - _loneliness_ will i have people around me?
 - _globilization_ will everything be ok?
 - _meaning_ is what i'm doing important?

it brings things down to a very abstract level - what is trust? how can
you define it in a satisfying way?

how about

> _trust_ is being able to relax about something important

... perhaps not the best explanation.

i think here _important_ is fine - you wouldn't really care to have trust
about things that aren't important... - but _relax_ is quite vague and
unsatisfying. really it means "you can trust it" but that's ridiculous to
say...

----

back to programming.

in software you create something - you assembly files, write code and
documents. you setup systems, write configuration. you push to a repository,
connect and setup servers, use online services. test, rewrite, analyze,
bug fix, try out different systems, languages, architectures.

but when it all comes down to it what we are really thinking before we
save, or push, or click deploy, is:

```
is this going to work?

```

in this context _trust_ becomes easy to define: how certain am i that
things will work as intended?

programming is difficult, because of complexity - so many things could
happen. a user could click a button multiple times. another one could
use an old browser. yet another could put text where a number should go.

and on and on we can describe all the multitudinous variables that we
should consider if we want to be sure that **under every circumstance**
things will work: the operating system, the number of users, the sequence
of interactions, the space left on the device...

but these are all _external_ forces - these are about the _real world_
interacting with our system. what about the system itself? surely that
we can control basically completely - it's all abstract and in our minds!
you can have any internal structure you want!

----

one word that pops up when talking about all of this is **options**.
(i am aware of emphasising too many words already).

by option i mean 'what can happen' and more than that, that 'what can happen'
is really a finite list that we can... list.

let's take the pure, lovely world of a programming language where we
can, apparently, decide on things in total and have all the time in
the world to make things perfect (and yet somehow still can't...):

```js
let x = 10
```

ok so this is Javascript which is dynamically typed. so you have types
but they are decided during execution (a really, really bad idea, but 
hopefully in this article i will convince you why).

so as this code runs the JS runtime will decide "ok so _x_ is an **integer**
and right now it has a value of _10_". (and here too _right now_ is *such*
a bad idea, for the same reason i will get into!).

ok. what are our `options` ? (i've found a new way to emphasize).

 - ..... well what do i mean by `options`???

perhaps this is a bad example to look at. let's look instead at this:

```js
let x = a + b
```

(Here i'm going to go much closer to the article i linked...)

So what _could_ be happening here?

- _a_ could be an integer, _b_ could be an integer ... so _x_ becomes an integer!
- _a_ could be a string, and _b_ could be an integer ... so _x_ becomes ... I dunno, a string? Concetenated?

Ok, and lot's more options, like `a could be undefined` and `b could be a boolean`.

What i'm getting at is thing:

> you are looking at some code.
> you wonder what is going on
> you are in javascript
> so basically you are fucked

that's one part of trust that i am have (finally) gotten to: what is it
like when you encounter some code? can you _trust_:

- what will happen
- what does it mean

----

**what will happen**

- will the code break?
- will the value be what i expect?
- will it work under all conditions?
- do i need to test this for various situations?

**what does it mean**

- how does this relate to the rest of my program?
- how much of an effect does it have to everything else?
- ...

(the _meaning_ part here is pretty vague... need to think if it's just part of _what will happen_...)

---

let's get back to the world at large.

so you're having a conversation with someone and you are wondering as well:
`what will happen`

- if i laugh, will they be offended?
- are they understanding what i'm saying?
- are they judging me right now?
- is this person about to stab me? are they getting really angry?

again, _trust_: you're looking at something trying to understand it. trying to
know something about the world and it's trajector, trying to understand how
things will behave in different context.

so perhaps this is a good definition of _trust_: knowing that something will
behave **consistently** `regardless of circumstance`.

---

it's these two that must happen together. even when something behaves consistently
is no guarantee that it will continue to! that is why _trust_ is about learning
about the unseen depths - someone can smile and be friendly for a long time but
you are still not safe because it's a vaneer. you need to have a sense of their
insides, the inner mechanics, in order to know "ok - this is not just a show or
dependant on this moment. this is stable, this is robust".

similarly with code - just because you're sysem has been humming along for a few
days and seems to be working does not mean it will not break when it encounters
a new circumstance.

so how do we get to know the 'inner workings' of something, of people or of code?

well for code i think i have an answer.