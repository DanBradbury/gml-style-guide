# The GML Style Guide

This GML Style guide recommends best practices so that GML programmers can write code that can be maintained by other real-world GML programmers. No matter how much work and love this style guide gets there is no way to reach a total agreement about all ways of solving problems.

The guide is seperated into sections of related rules. Each added rule should have a rationale included behind the rule (unless it's obvious).

The basic format is based on bbatsov's ruby-style-guide and is meant to serve as a growing document to reflect the GM workflow.

## Table of Contents
* [Source Code Layout](#source-code-layout)
* [Project Structure](#project-structure)
* [Syntax](#syntax)
* [Naming](#naming)
* [Comments](#comments)

## Source Code Layout
> Nearly everybody is convinced that every style but their own is
> ugly and unreadable. Leave out the "but their own" and they're
> probably right... <br/>
> -- Jerry Coffin (on indentation)

* Use two **spaces** per indentation level (soft tabs). No hard tabs.
```c
// bad - four spaces
if(something) {
    do_things();
}

// good
if(something) {
  do_things();
}
```

* Don't use `;` to seperate statements and expressions. Use one expression per line.
```c
// bad
image_index=0; image_angle+=2;

// good
update_image();
handle_gravity();
```

## Project Strucutre
All objects should have their code moved into individual scripts.
We do this to allow programmers to use the editor of their choice and have and be able to see all the code directly in the associated gml script files.

* Example:

**obj_map**
```c
/* create event */
map_create();
/* step event */
map_step();
/* draw event */
map_draw();
```

## Syntax
* Conitionals (`if/else/else if`) use the same block structure. The `{` & `}`  are used to explicitly state the enclosing body.
```c
// bad
if(test_truthy)
  {
  ...
  }

// better but still bad - extra line mucks readability
if(truthiness)
{
  ...
}

// good (space after condition is preference)
if(truthy) {
  ...
}
```
* Use `!` instead of `==false`
```c
// bad
if(JUMPING == false) {
  ...
}

// good
if(!JUMPING) {
  ...
}
```
* In a similar vain never use `==true`
```c
// bad
if(FALLING == true) {
  ...
}

// good
if(FALLING) {
  ...
}
```

## Naming
* **objects** should be named with `obj_` prefix
```c
// bad
o_box
object_box
box

// good
obj_box
```

* **sprites** should be named with `spr_` prefix
```c
// bad
s_box
sprite_box
box

// good
spr_box
```

* **backgrounds** should be named with `bg_` prefix
```c
// bad
b_box
background_box
box

// good
bg_box
```

* **scripts** created to hold code for objects should be named with  `objectName_eventName`
* With an object named `obj_player` our script for create would be `player_create`

## Comments
> Good code is its own best documentation. As you're about to add a comment, ask yourself, "How can I improve the code so that this comment isn't needed?" Improve the code and then document it to make it even clearer.
> -- Steve McConnell

* Write self-documenting code!!
* Write comments in English
* Use one space between the leading `//` and the comment text
* Avoid superfulous comments
```c
// bad
counter += 1 // increment counter by 1
```
* Keep comments up-to-date. An outdated comment is worse than no comment at all
* Avoid writing comments to explain bad code. Refactor the code to make it self-explanatory
