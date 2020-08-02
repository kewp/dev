---
title: goal fix.txt
date: 2020-05-14
tags:
layout: layouts/post.njk
---

i've spent what is coming on a year trying to solve this one problem
which is basically "give me this feature set"
specifically a charting program written in javascript.

it started out written one way
and i found the code so confusing
i decided to rewrite it completely
and the rewrite turned into such a disaster
which really is on going
that i have this desperate sense of
"what did i do wrong? how do i fix this? why is this so bad?"

and i keep getting reminded over and over of the problem
but haven't specified it yet, and keep getting more opportunities.

today i'm fixing the comparisons
(which amazingly is still the feature that was added originally)
and the colors are not coming out right - when you remove one
comparison all the colors of the existing charts change,
which is confusing (and just wrong).

so i look at where the colors are being generated
and it's a mess - it's in one part of the code
which is triggered by another
and i have this feeling whilst i'm trying to fix it
that i don't really understand my code - i don't
really know what the part i'm working on is going
to do to the rest of the code.

here is where i'm trying to zoom onto - this feeling,
this bad sense: not knowing the effects of what you
are doing. not having a total understanding. not
being able to trust the connections.

how do i know that the code i just touched isn't going
to break something else going forward? that some edge
case will randomly break it?

why do i feel like i don't understand my code?
that some issue will come up randomly
and i will just have to fiddle until the problem goes
away (if i'm lucky enough to be able to reproduce it
locally!) and if the problem does go away i'm not
even sure what was causing it.

that is the situation i'm in - blind.

how do i encapsulate this idea - what is the simplest
way to illustrate being 'blind' as a coder...

yes, if i was more intelligent i could follow the threads
more fully. i could see the second and third level
connections. but then as my code grows in complexity
it could still reach the limit of this - the amount
of indirection can always climb.

yes, this is what functional programming purports to
solve, with notions of immutability and pure functions,
but i haven't found any of this is caused by having
impure functions. it's not a local issue, it's not
just this piece of code i can't understand. i understand
my functions just fine. what i don't understand is
my program - the entire thing.
more functional programming seems to me would make the
program i'm describing even worse - indirection piled
ontop of more indirection. when i click on something,
when i fire off something like "remove this chart from
the graphs" - what happens? what does it touch?
if i'm editing this code - what will it affect?

i've been hitting my head against this for so long now.
i've watched hours of videos of functional techniques,
on algebraic types. even when i started the project this
was my main goal - how do i take the code that was there
(build mainly out of events and huge functions) and
make it easier to understand - to be able to focus
on just each piece without having to hold all these
other pieces in my head. joyful programming, as blow says.

again, the same thing is going on here as i've been
saying since the beginning - what the fuck is going on?
why is this so difficult? why am i constantly finding
myself 'hacking' the code, wishing it worked, not
feeling confident about it, dreading any problems
that come up. this frankenstein.