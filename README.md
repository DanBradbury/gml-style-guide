# The GML Style Guide

This GML Style guide recommends best practices so that GML programmers can write code that can be maintained by other real-world GML programmers. No matter how much work and love this style guide gets there is no way to reach a total agreement about all ways of solving problems.

## Table of Contents
* [Source Code Layout](#source-code-layout)
* [Syntax](#syntax)
* [Naming](#naming)
* [Comments](#comments)

## Source Code Layout
> Nearly everybody is convinced that every style but their own is
> ugly and unreadable. Leave out the "but their own" and they're
> probably right... <br/>
> -- Jerry Coffin (on indentation)

* Use two *OR* four **spaces** per indentation level (soft tabs). No hard tabs.
  * consistency is key so pick something and stick to it! (I prefer 2 :D)
```c
// bad - four spaces
if(something) {
    do_things();
}

// good
if(something) {
  do_things();
}

// also good
if(something) {
    do_things();
}
```

* Don't use `;` to seperate statements and expressions that convey have larger implications than setters. Use one expression per line.
  * if actions are logically grouped use proper spacing (ie. `a=1; b=2; c=3;`)
```c
// bad
update_image(); handle_gravity();

// good
update_image();
handle_gravity();

// fine (simple actions that are logically grouped)
image_index=0; image_angle+=2;
```

## Syntax
* **Conitionals** (`if/else/else if`) use the same block structure. The `{` & `}`  are used to explicitly state the enclosing body.
```c
// bad
if(test_truthy)
  {
  ...
  }

// good (not my ideal but readible)
if(truthiness)
{
  ...
}

// good (space after condition is preference)
if(truthy) {
  ...
}
```
* Use `!` instead of `== false`
```c
// bad
if(jumping == false) {
  ...
}

// good
if(!jumping) {
  ...
}
```
* In a similar vain never use `== true`
```c
// bad
if(falling == true) {
  ...
}

// good
if(falling) {
  ...
}
```

* **Simple Operations** (i=i+1, i+=1, i++) should always use the optimal pattern.
```c
// bad
i = i + 1; // should only be used for complex arithmatic that cannot be reduced to a more efficient pattern.

// good
i += 1; // best used when adding a single constant or variable other than 1 

// better
i++; // optimal when incrementing a variable by one.
```
* For simple operations, although they appear to produce the same effect, each instruction corresponds at a low level to a different way of interacting the the processor. 
* The same applies for subtraction (i=i-1, i-=1, and i--);

## Naming
* **variables** should be all lowercase, with underscores between words. 
```c
// bad
tablename

// better, but bad (leads to tablename typos)
tableName

// best
table_name
```

* **local variables** can be identified with a leading underscore.
```
// instance variable
instance_variable_name

// local variable
_local_variable_name
```

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

* **scripts** should be preceded with scr_ prefix followed by mixedcase naming
  * In many cases you might want helper functions like `pack` to be a script. This is perfectly fine as long as an appropriate comment is added to the file


* **macros** whose value is fixed for the duration of the program, should be named using all caps.
```c
// bad
out_of_memory = 1

// better
OUTOFMEMORY = 1

// best
OUT_OF_MEMORY = 1
```

* **enumerators** should be named like macros, using all caps. The enumeration name should use mixed case. 
```c
// bad
enum rainbowColors {
  red = 1,
  blue = 2
}

// good
enum RainbowColors {
  RED = 1,
  BLUE = 2
}
```

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
