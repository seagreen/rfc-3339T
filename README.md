# What's this?

A variant of RFC 3339[1] that's a strict subset of ISO 8601[2].

[1] https://tools.ietf.org/html/rfc3339#section-4.3

[2] https://www.iso.org/iso-8601-date-and-time-format.html

# Motivation

https://news.ycombinator.com/item?id=26401261

# Definition

RFC 3339T is exactly like RFC 3339 with the following exceptions.

## T separator

Date and time MUST NOT be separted by a space.

This part from section [5.6](https://tools.ietf.org/html/rfc3339#section-5.6) is struck out:
```
NOTE: ISO 8601 defines date and time separated by "T".
Applications using this syntax may choose, for the sake of
readability, to specify a full-date and full-time separated by
(say) a space character.
```

## No negative zero offsets

Section [4.3](https://tools.ietf.org/html/rfc3339#section-4.3) is struck out:
```
If the time in UTC is known, but the offset to local time is unknown,
this can be represented with an offset of "-00:00".  This differs
semantically from an offset of "Z" or "+00:00", which imply that UTC
is the preferred reference point for the specified time.
```

Since this isn't allowed by ISO 8601 we can't allow it here.

Use some other channel to communicate this information.

# Note on minimalism

The goal of this specification isn't to be the most minimal subset of RFC 3339 that can still communicate all the relevant information.

Rather, it is make RFC 3339 just small enough that it becomes a strict subset of ISO 8601.

For example, RFC 3339 allows the "T" separator to be either `T` or `t` (as explained in the NOTE in section [5.6](https://tools.ietf.org/html/rfc3339#section-5.6)). We allow that as well since it's allowed by ISO 8601.

If a different project wants to make the smallest RFC 3339 possible for outputting according to [Postel's Law](https://en.wikipedia.org/wiki/Robustness_principle) please let me know about it.

# Development

This specification is experimental and subject to change for now.

However, in about 6 months (September 2021) we'll update this document declaring it frozen. After that point we won't make any more changes, so if you have suggestions please make them now!

# Caveats

Not an official RFC.

# Special Thanks

[joshuaissac](https://news.ycombinator.com/user?id=joshuaissac) for [this suggestion](https://news.ycombinator.com/item?id=26401345).
