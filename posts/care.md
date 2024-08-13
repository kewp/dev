---
title: care.txt
date: 2024-08-12
tags: dev
layout: layouts/post.njk
---

i have this job. well, i had a request
from tom:

```
https://trade.undercurrentnews.com/?regions=United_States_of_America&flow=Export&products=0303390130&view=barline&group_by=regions&value_volume=value&total_per_volume=per_volume&frequency=Monthly&currency=USD&unit=metric_ton&extended&enddate=May_2024
11:10

@Karl
 only May showing here
11:10
on extended
```

so there is no june data for this product ...
which means something is up.

now i need to do several things - well, firstly,
i need to stare at this and figure out: what do i
need to do?

and it's the same thing over and over ... and it's
stressful. it's time consuming. i have a lot of
other stuff to do ... and each time tom asks me
this i feel bad, feel guilty that something isn't
working ... i told him i would sort this out and
it keeps happening ...

and every time it's the same story: sit and stare
at it, think to myself "ok, trade portal ... hmmm ...
what do i need to do ...". then realise, oh - i should
check if the us census api has this data ... if not,
problem solves: "tom, the us census hasn't published
june data for that product code yet" ... nothing i can
do.

however, if the census api does have june data ...
then there is something wrong with the importer ....

and then i have to sit and stare and think - ok, how
does the importer work? i've got so many importers
running, they're all really complicated, so every time
i have an issue with this it's like turning an oil
tanker, it takes forever to really understand it, remember
all the complexities, what goes where, which machine is
running what, how does it cache, what databases, what
scripts are running, how ...

and each time it's this manual thing - ok, i need to
check the api script ... how does it work ... click,
try to remember which repo holds the code ... often
this whole process is me just staring at my computer
stupidly, waiting for my brain to give me an answer ...

i remember "oh, i think it's `trade_portal_data`...".
i open that one up in my editor. look at it ... hmmm
that code doesn't look right ...

"oh" i say to myself, "i should go onto the machine
and see what is inside of cron" .... i ssh into the
machine (if i can remember the alias i gave it) ...
go into cron ... ah, yes - this looks right ...
ok, there it is: trade_portal_data/uscensus/import.py ...

now i know where the code is ... i open the code up ...
scroll down ... i'm trying to figure out where it
connects to the database, how do i save the connection
string? ah, it's using filenames `TARGET_DB_HOST`,
`TARGET_DB_USER`, etc ...

i go back into command line, into the server, cd into
the source folder, cat out those files ... right, i
now have the strings of the db url ... i can now
connect. let's see if i can do it from my own computer ...

...

holy shit. i've just gotten started.

and i do this _every fucking time_ ...... and what i
want to know is: why?

why have i not stopped and asked myself - couldn't i
figure out a way to do this automatically? it's what
i do, i automate things ... why haven't i, after all
this time, not written a script to do just that?

and i think the truth is that i haven't just sat and
acknowledged how stressful this is. i just ... somehow
never even thought ... to see it that way. it's not
even a thing ... but why? why do i allow myself to suffer
like this? why does it not even register: karl, this
is insane. this happens every few days? holy shit ...
i hope you're being paid a lot! isn't there anything
you can do to mitigate this?! this is crazy!

i ... if someone had said that to me, or anything like
it ... i would have looked at them like _they_ were
crazy ... what do you mean, intense? i love it! it's
fine ... yeah, it's pretty nuts but that's my job,
that's what i do ... i would have brushed it off,
minimised it, passed over it, justified it ... basically
not have registered what the person was saying, what
they _saw_ .... they saw something and it was simply
a case of politeness that made it easy for me to
ignore their trying to help, telling me something i
was clearly blind to, something important ...

care. the truth is that i simply didn't care whether
i was under pressure or not ... it never occurred to
me to care ...

which is bizarre. saying "it is what is is" is bullshit.
i can solve this. i can easily solve this. i can do it
in an hour - just create some code, go through all the
steps i normally need to perform, put them into a script ...
and tada! all these hours of future stress and pressure
and anxiety and shame - gone. just like that.

and yet somehow i would have confidently told you to
fuck off if you had suggested there was a better way ...
had suggested i was doing something completely irrational,
something that was self harming for no reason ...
isn't that crazy?

and if you look at this, and imagine that ... if i'm doing
this here, in this particular instance ... there's a good
chance i'm doing it elsewhere as well ... how ... how much
stress and pain and suffering and shame ... am i simply
letting myself go through, through neglect? through pointless
neglect ... ?