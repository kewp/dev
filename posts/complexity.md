---
title: complexity.txt
date: 2020-05-19
tags: dev
layout: layouts/post.njk
---

i wonder if the allure of technology for me as a child was
that i thought i could encapsulate it.
with maths too. i saw how you could build massive things
with this small parts, and here is my mistake - i thought
because i understood the small parts that i could
understand the whole. more than that - i felt like i could
see the whole. and now i'm starting to see how that was
an illusion, or better a self delusion.

it's easy to show. take anything small and build from it.
i think this is what 'logic' really means.

bill started heavier than ted.
ted just gained fourty kilograms.
bill and ted share clothes when they are the same weight.
when bill and ted share things they fight.
ted gains weight when his mother is depressed.
bill and ted fighting makes his mother depressed.

a graph is a set of numbers.
each number has a date.
when you draw a graph you show just the values between two dates.
each date is a year and period
the period can be months, weeks or quarters.
graphs belong to a dataset.
each dataset has a frequency, showing what the period means.
graphs can be classified by their product.
you can have multiple graphs with the same product but different frequencies.
when you draw more than one graph you should show them with the same frequencies.

god i just started talking about this
and already it's clear how insanely complicated this is.
i can't believe i thought this was straight forward.

---
i can't believe i thought this was easy.
---

you have structure, you have rules, you have events.
and somehow i've grown up with this idea that because the pieces were so straight
forward that using them would be too.

maybe it is - maybe i saw something true
but i have been doing this a long time
and it certainly isn't easy for me.
it's like a game - a challenge to myself.
and i never recognise how the more parts you have the less easy it is for me.
the more help i need. the more disciplined i have to be.

it's this blind spot that i want to enscribe, to at least shade around
so i can see it's outline.

a and b are whole numbers.
they map into another set of numbers.

i feel like i'm trying to solve complexity.
to find a skeleton key that unlocks all of it.
'follow this procedure and you won't have problems
building hugely complex things again'.
and i am surrounded by people (men) who feel the same way
like they are just around the corner from doing just that.
that this is easy. they all (we all) have a feeling that
it's almost there, we can just about see it.

and i feel it right now. this issue with work.
once again - if i just encapsulate this, wrap everything up,
break it down, separate and define, limit the interface,
then i can look at one piece at a time and not worry about
the rest.

that's what i want - to stop worrying.
to feel like i see everything.
that if i've made a mistake it's local. it doesn't break everything.
that it's not all tied together like a house of cards.
because of the way things are built.
mistakes are inevitable but you can mitigate their effects.
there are approaches you can take to building things
procedures, practices,
that ensure things. you can ensure things by design.

what do i want to ensure?
what type of things can i ensure?

i can ensure that ... things happen in a particular order.
i can ensure that ... all the items in a chart have the same frequency.

ok, main_charts:

 - any change to it must be atomic: a single function that returns a result
 - that way, i can check the return value for the property i'm trying to ensure

```js
function maincharts_frequencies_match(maincharts)
{
	// always put these in to get a nice stack trace
	// (don't let javascript fail for you)
	
	// return false if validation fails
	// (i.e. won't update object)

	if (!assert_exists(maincharts)) return false;
	if (!assert_object(maincharts)) return false;
	if (!assert_nonempty(maincharts)) return false;

	let main = maincharts[0];

	if (!validate_dataset(main)) return false;
}
```