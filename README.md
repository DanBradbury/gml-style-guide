# The GML Style Guide

This GML Style guide recommends best practices so that GML programmers can write code that can be maintained by other real-world GML programmers. No matter how much work and love this style guide gets there is no way to reach a total agreement about all ways of solving problems.

The guide is seperated into sections of related rules. Each added rule should have a rationale included behind the rule (unless it's obvious).

The basic format is based on bbatsov's ruby-style-guide and is meant to serve as a growing document to reflect the GM workflow.

## Source Code Layout
> Nearly everybody is convinced that every style but their own is
> ugly and unreadable. Leave out the "but their own" and they're
> probably right... <br/>
> -- Jerry Coffin (on indentation)

* Use two **spaces** per indentation level (soft tabs). No hard tabs.
```gml
/* bad - four spaces */
if(something){
    do_things();
}

/* good */
if(something){
  do_things();
}
```

* Don't use `;` to seperate statements and expressions. Use one expression per  line.
```gml
/* bad */
image_index=0; image_angle+=2;

/* good */
update_image();
handle_gravity();
```

## Project Strucutre
All objects should have their code moved into individual scripts.
We do this to allow programmers to use the editor of their choice and have and be able to see all the code directly in the associated gml script files.

* Example:

**o_map**
```gml
/* create event */
map_create();
/* step event */
map_step();
/* draw event */
map_draw();
```

