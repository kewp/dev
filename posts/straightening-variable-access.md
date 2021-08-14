---
title: straightening variable access.txt
date: 2021-08-14
tags: dev
layout: layouts/post.njk
---

i think i've just discovered something remarkable.
i think i've just realised that what i've done
though my `auto` library really is a way to
untangle any code, to take any system and
remove it's complexity. it's like a place to
stand - once you have a foothold you can iron
out everything in a procedural way.

i'm busy rewriting an old project, the bug bear
that caused this entire endevour, i've ranted
about it at length, for years i tried to figure
out how i got so entangled in complexity and
obsessed about what a solution might look like.
and today i decided to take my weekend to
go at it, to apply this technique to the old
project. i expected it would be painful - after
all, the old project is complex beyond to the
point of total mental collapse. i almost want
to 3d print it and put it on display it's so
crazy how intertwined and impossible to
understand it is.

but just as i started something bizarre struck
me - ironing it out was completely straight
forward. i'm struggling to capture it - it
fell out and integrated and flattened my code
directly ... naturally ... i'm not sure how
else to put it but that i was shocked at how
quick it was. it's as if the complexity wasn't
really there - i suppose i figured that the
process of fixing it would be as difficult
as how badly the program had been written,
but i found that this was not the case. so
this is my amazed sense - that simplifying
a piece of software is unrelated to how
complex it is. could that possibly be true?
that just seems ... wrong ... but bizarrely
it seemed to make a kind of somatic sense
when i watched the complexity of my old
project fall away by laying down the lines
of variable logic ...

of course i need to provide an example. this
can only be anything more than just an
entertaining fever dream if i walk through
a piece of complex code and straighten it
out. but even then i can see reactions of
specificity - that it will inevitably only
show one case, the case i'm showing.

i want to post this on hacker news. i'm so
excited i'm finding it hard to type. i can
see it in my mind. it's so straight forward
it's unnerving. what software is is really
the simplest thing.

it must be driving people nuts, anyone reading
this. what the fuck are you talking about?
i get it. i get that i sound insane, i get
that teenage geeks say this stuff invariably
at some time in their lives (i'm not a teenager,
btw). i get that your mind is shooting in
various directions trying to categorise this,
trying to make sense of it - which box does
this rant fall into. i do exactly the same
thing. and now i'm falling into that cult-y
kind of reassuring intelligent convincing
vibe too.

but i really, truly don't know how to convince
anyone of what i'm saying. i can show you code,
yes - i will endevour to do that. but every
time i think to do that, and i have (i have
published a library for this!) invariably it
becomes clear that no one is going to be
convinced by it.

how to convince people? really i don't know.
the best i can imagine is to do it mathematically,
that is to say - undeniably. to somehow codify
software and then say "if you accept this then
look - it follows that i must be right". ok.
i mean, how much effort do i have to put in?

what an insane rant. without giving up the
goods. ok fine - i'll try again to hash this
out. i'm just going to fling mud at the wall
and see what sticks. and then i'll see if i
have the guts to post this to hacker news.

## mud at the wall

define your variables in terms of functions.
for example, i have a variable called `name`
that is used through-out my project. the
issue, as i've talked about ad-nauseam before,
is that it is set at different points in the
program. and the solution (and i mean _the solution_
as in _this is the solution to ALL complexity!_)
is to have a single point at which the
variable is determined, a single path, a
single _function_ if you will.

how can i write this out in code?

```js
let name = 10;

function blah() {

    name = name * 2; // bad
}
```

i think really i should just keep posting these
things to hacker news and just deal with the
misunderstanding and my inability to communicate
my ideas. oh man how intense.

## files everywhere

ok, think about one of your software projects,
something you have to maintain but which is
a nightmare because every time you need to
look into it, every time you have to change
something it feels like a house of cards, it's
as though touching one thing could break another,
you have no idea how the thing works because
it's a bohemouth, because it's just this
insane mess of wires everywhere, this labyrinth
of causes and effects, of pieces doing one thing
connected to others ... can you imagine it?
do you have one in mind?

now of course i suppose there could be some people
who do not get into this problem. and i should
accept the possibility that perhaps the majority
of my audience is like this - maybe the peeps
on hacker news are all way better programmers
than me and i'm just embarrassing myself, i'm just
showing how unsophisticated i am, software is easy,
if your projects turn into a horrible mess then
you just aren't a good programmer, you don't think
well. ah man, well that could be the case. and
if so - i invite anyone who is not one of these
superior beings to follow me through to solutions-
for-stupid-ville! come with me, i think i've
devised a solution for our disabled asses to 
operate the door handles...

ok so if you're still reading then you have in
fact found that most of the software you have
worked on for enough time has turned into a
maintenance nightmare, a garbled mess, even
though you've tried all the techniques everyone
says you're suppose to - object orientated code,
functional programming, different languages,
the unix principle maybe ... if you're with me
then you too have just found each thing you
try to do just collapsed under the weight of
complexity. somehow your projects all get
away from you no matter how much you focus
on the design choices up front.

ok. so from this humble starting point i submit
that i may have found something that underlies
this problem, i may in fact have found _the_
reason software goes ary. i know how this sounds.
and i admit i could be wrong and this could be
nothing. but if you're curious and have any
sense that i may be worth listening to
then i invite you to follow me down a rabbit
hole.

## the hole

to start you need to understand where i'm coming from.
i write software for a living and for the
last few years have been working for the same
company doing data visualization. so i had to
make a web app that displayed charts. i've
been writing software professionally for about
10 years, before that i did a masters in
numerical simulations, and before that i was just
a geek in love with computers.

anyway. this whole deal i'm on started when my
lovely boss asked me to take a look at the charting
software she had written. she wanted me to add
a feature and i looked at this thing and was like
"this should be easy". turns out it wasn't - it
took me three years to get the thing right and
all this after having been a software developer
for so long, it really made me wonder - why on
earth did such a simple task buckle me? what
happened? (i have ranted and raved about this
before, i think perhaps on this blog?)

ok so let me just jump in then - this "solution"
i have "found" has only been applied to this
small subset of things: web apps that do
visualisation. so it's javascript, and it's
data manipulation. the problem i've used this
on boils down to:

```
json -> variables -> dom
```

that's an oversimplification. in fact, i
use Svelte to render to the dom, so it's saying
too much, even.

but my point is - even if i have somehow stumbled
onto this clever way of solving things it could
turn out that i just solved how to, i dunno,
write out data transformation rules in a consistent
way. or perhaps this stuff will only apply to
javascript somehow.

to be honest, though, that is not the sense i get.
the sense i get is that there is something deeper
here, some kind of simple but unrecognised truth
about software that is hard to describe because
it's new but once dealt with enough times will
become almost obvious. like the jump from
writing things in binary to using symbols. we
don't talk about why we did that, why we don't
use binary - it's obvious why ...

## give me the juice

i feel so panicked at the prospect of actually
posting this to the forum.

i know anyone reading to this point is like "well
what on earth it _it_ ?!?" and there are a million
things i could say, and i have said them, and
i've produced a library explaining it, and how
much more do i need to do in order to get
someone on board.

ok, how about this: you know that insanely complex
project you have that you don't want to touch?
ok - i know how to make it the most benign thing
you've ever made. i know how to take away all
that dread, all that anxiety. i reckon i know
how to make it the most easy to understand project
you are looking after, and that the process of
converting it to do so is totally straight
forward and painless.

right, but here is the catch - the boilerplate.
you have to have my thing in your system,
or something like my thing. i've only written
it for javascript (i've sort of started on
a python version). and i've only used it on
a svelte front-end! so yes - if i really want
to prove my point and get people to try it
then i have to have worked on a react project
and a vue project and applied it to that ...

but fuck me, really? i have enough shit to do.
when am i going to get the time to use react?
fuck i suppose i should use react in my next
project at work ... what a pain that will be,
i don't know react!

ok, anyone out there still reading who's
bohemoth project is written in Svelte? ok
here is what you do:

## svelte users

create a file called `state.js` which looks like
this:

```js

import auto from '@autolib/auto';

export default auto({

});

```

create a file called `state_key.js` and put in
the following:

```js
const contextKey = {}
export default contextKey
```

> this just ensures you have a unique key no matter how many instances
> of your app you create ...

now inside of your `App.svelte` put the following:

```js

import state from './state.js';
import key from './state_key.js';

setContext(key, state['#']);

```

god this is too much effort. i mean, really.


## boilerplate done

right, that's it for the boilerplate.

now somewhere in your program, in one of your other Svelte
files put:

```js

import key from './state_key.js';

//const { } = getContext(key);

```

