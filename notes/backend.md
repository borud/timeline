# Backend notes

The backend should have two parts which are somewhat separated from
each other: the timeline part and the media part.

Since the timeline itself is the key part I would prioritize building
this first and then, optionally, build the media handling part since
the only real requirement for the media parts initially is that they
are reliably accessible and downloadable.

## Keep Focus.

Also be careful about adding features that are not strictly needed
until later.  Start simple and then evolve it later.  Developing a
sensible timeline data model is the hard bit -- developing tools to
transform, interpret, improve and process media is a lot of work, but
it isn't what is entirely new here.

## Simplicity

### Backend Interface.

The main interface for the backend should be a
[REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
API since this is a well established architecture for managing
information on the web.  When designing the API it would be preferable
to try to stick as closely as practical to proper use of REST.  This
implies that developers understand the
[HATEOAS](https://en.wikipedia.org/wiki/HATEOAS) constraints and can
make intelligent choices with regard to how closely to follow the
principles.

### API Data Format

Rather than support many different kinds of metadata formats for use
in the API, I would suggest sticking to
[JSON](https://en.wikipedia.org/wiki/JSON) since this is perhaps one
of the simplest and most widely accepted formats which is also human
readable.

### Data Model.

It will be tempting to put many moving parts and much abstraction into
the model.  I would advise against this since too much abstraction
tends to take focus away from producing something that is actually
workable.  Start simple and try to reach plateaus where we have
something that works. Introduce abstractions when there is a definite
need.  Don't be tempted to introduce abstraction just to scratch some
intellectual itch -- wait until an implementation drive need arises.

Eg. call a person a person.  Not an actor or some other abstraction.
We will need abstractions for lots of things, but we can add, redesign
and reorganze later.

Which brings is to the next thing to note:  the data model must have
high degree of plasticity.  Assume things will change and rather than
trying to make the perfect data model from the outset, try to imagine
and anticipate how it will evolve.

# Misc notes

Whenever we need to express something like time, place,
characterization of media files etc, we should look at what is in
common use.  Choosing something that is in common use rather than
constructing something specialized that is "perfect" means we can
leverage the work of others -- which is important in order to make
this practical.

Not least because dealing with something like time turns out to be
very complicated.

## Representation of time

For all representations of time the system should use the
[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standard
exclusively.  Or rather, for each use there should be a clearly
defined part of that standard used.  So for instance points in time,
intervals etc are always written the same way.

Note that internal representations of time in the software will be
implementation specific.  For instance, many systems use number of
seconds or milliseconds since epoch as their internal representation.


## Media and media types

Being able to describe media content precisely will be key for a
system that has to deal with recordings of different kinds.  One of
the more widespread standards is the
[MIME](https://en.wikipedia.org/wiki/MIME) standards.


