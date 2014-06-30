Bad Inheritance from Java
========================

  - Blockless statements
    - if (foo) bar();

  - Expression statements
    - foo;

  - ++ and --
    - Convient, but cause so many buffer overloads or security flaws

  - switch
    - can have fall throughs in your statements, however this can lead to really bad results

## Good Parts
  - Lambda
  - Dynamic Objects
  - Loose Typing
  - Object Literals

### Data type conversion / dynamic objects

    var answer = 42;
    answer = "Bring your towerl...";

    "37" + 7
    "37" - 7

#### Literals
```javascript
var places = ['hong kong', 'china'];

places = [, 'australia', , 'japan', 'hawaii'];
```
## Bad Parts

    // js inserts semicolons;
    // bad style can equal bad results
    return
    {
      ok: false
    };

    return {
      ok: true
    };

## Downside for JS Animations

- CPU Intensive
-

Relative Positioning
The Good:

Resizing of relative elements affects document flow (fluid layout)
The Bad:
Easily very CPU-intensive if many elements are involved/layout is complex
The Workaround:
Absolutely-position animated element containers (or single elements to be animated) wherever feasible. This will "isolate" the elements in question from the normal document flow, minimizing the amount of reflow calculation done by the browser.
Browser-Rendered Visual Style - CSS
The Good:

Content separate from presentation
Visual style handled by CSS, can be easily re-used elsewhere
Self-explanatory
The Bad:
Opacity and background images (depending) can seriously degrade performance
The Workaround:
Performance can be compared between PNGs and CSS opacity/filters; mileage may vary depending on circumstances
CSS Class Swapping
someDiv.className = 'moving';

The Good:

Good for a one-time "set and forget" change, eg. active vs. inactive
The Bad:
Slow as hell, especially if every animation frame/loop involves a class name change
Browser must re-evaluate CSS rules related to this class and child DOM elements of the targeted element, and other CSS rules which may apply, eg. div.someClass, div.someClass img { background:#ff3333; }
The Workaround:
Use script to apply visual style change directly to the element in question, avoiding class swapping altogether; eg. someDiv.style.backgroundColor = '#ff3333';. This may also apply to element ID swapping.
Background Images
#someDiv { background:transparent url(/some/image.gif) no-repeat 0px 0px; }

The Good:

Can save an extra <img /> element from being used. Position/tile attributes are easily adjusted.
The Bad:
Redraw (animation) appears to cause "wait" cursor flicker under Internet Explorer; usually more CPU-intensive than using <img />.
Image cannot be stretched with this method.
The Workaround:
Substitute with <img /> where tile is not necessary or if stretching is desired.
If adjusting image positioning, use an absolutely-positioned image within a fixed-size, cropped container rather than background x/y.
