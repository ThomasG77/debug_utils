Debug Utils
-----------

Useful JavaScript debug utilities.

__Currently works well in chrome but will bring this to more browsers soon.__

## Event Debugging

As the complexity of a system grows, evented programming can make it very hard
to debug. The following utilities should help you:

### $duv(object, event)

Attach an event handler that starts debugger when trigerred.

Usesful for:

* Making sure the event is being trigerred.
* Stepping through other event handlers.
* Finding out what trigerred the event.

### $duvl(object, event)

Attach an event handler that logs its arguments when fired.

Usesful for:

* Making sure the event is being fired with the correct args.

### $duvr(object, event)

Remove previously set debug event handler.

## Debugging Property Access

Often times you find that some object is changing from under your feet. And you
need to find out what is changing that object. These are utilities for you:

### $dug(object, property)

Debug when something tries to get at a `property` of an `object`.

Useful for:

* Knowing which parts of the code is using your object.
* Tracking the value over calls and time.

### $dugl(object, property)

Like `$dug` but adds logging instead of `debugger`.

### $dugr(object, property)

Removes getters set by `$dugl` and `$dug`.

### $dus(object, property)

Debug when something tries to set a `property` on an `object`.

Useful for:

* Knowing which parts of the code is mutating yo shit.
* Tracking values set over time.

### $dusl(object, property)

Like `$dus` but adds logging instead of `debugger`.

### $dusr(object, property)

Removes setters set by `$dus` or `$dusl`.

### $dugs(object, property)

Debug both getter and setter. It's like calling `$dug` and `$dus` on an object.

### $dugsl(object, property)

Like `$dugs` but adds logging instead.

### $dugsr(object, property)

Removes getters and setters set by `$dugs` and `$dugsl`.

## Method debugging

The JavaScript command line API provides really nice utilities for debugging
functions:

* `monitor`|`unmonitor`: logs function calls.
* `debug`|`undebug`: adds a breakpoint on the first line of the function.

However, they don't work for native methods. The following should help:

### $dum(object, method)

Wraps an object's method with a wrapper function with a `debugger` statement.

Useful for:

* Debugging native methods: `$dum(Event.prototype, 'preventDefault')`

### $duml(object, method)

Like `$dum` but logs arguments instead.

### $dumr(object, method)

Removes debug or log wrappers added by `$dum` or `$duml`.
