<h1 align="center">New in Scribble 5.x.x</h1>

Scribble 5 contains some big changes compared to previous versions. The goal with Scribble 5 was to bring the library closer to how GameMaker's native `draw_text()` is used but without compromising on the efficiency of the library, or the range of effects possible.

`scribble_draw` is now substantially simpler compared to `scribble_create()` found in previous versions of the library. All customisation for Scribble is now done through draw state functions, very much like GameMaker's native draw state. For example, `scribble_draw_set_transform()` allows you to rotate and scale your text for zero extra cost, and `scribble_draw_set_blend()` controls the global colour/alpha blending of drawn text elements. This makes code substantially easier to read and should feel familiar to any GM dev.

`scribble_create()` and `scribble_destroy()` are gone and you now no longer need to worry about cleaning up memory unless your memory budget is very tight. Scribble 5's timed cache takes care of memory management for you: a new text element is created on demand by `scribble_draw` and, if that text hasn't been drawn for 15 seconds, that memory allocated for that text element is freed from the cache (this time limit is customiseable). The text creation/parsing portions of the library have been tripled in speed when running in YYC to accomodate this just-in-time text creation process.

The typewriter and event functionality in 4.x.x has been kept as well. This is now called `autotype`. Autotyping can still be applied per-line or per-character. Events are now trigged via `scribble_draw()` rather than a separate script\*. You'll need to pre-cache a text element (for example, running `scribble_draw()` in a Create event) and then use `scribble_autotype_set()` targeting that text element to start the typewriter effect.