- Feature Name: liner-syntax-highlighting-closure
- Start Date: 2018-06-7
- RFC PR: (leave this empty)
- Redox Issue: (leave this empty)

# Summary
[summary]: #summary

Add to liners function `read_line` an argument that contains a closure.

# Motivation
[motivation]: #motivation

It will allow us to improve ion's syntax highlighting. We want to see pretty colors while using ion. :)

# Detailed design
[design]: #detailed-design

Add an argument to liners `read_line` function that contains a closure. The type of the new argument will be `Option<Box<Fn(&str) -> Cow<str>>>`. `Option` so that if users of the library dont want to supply a closure they dont have to. `Box` to allow us to store the closure in the `Editor` struct and the closure returns a `Cow<str>` so that we dont have to return a heap allocated `String`.

# Drawbacks
[drawbacks]: #drawbacks

Performance will be impacted, especially if a complicated closure is supplied.

# Alternatives
[alternatives]: #alternatives

What other designs have been considered? What is the impact of not doing this?

# Unresolved questions
[unresolved]: #unresolved-questions

Is there a nicer way of doing this? `Option<Box<Fn(&str) -> Cow<str>>>` is a rather ugly type to deal with.
