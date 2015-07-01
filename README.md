jQuery-select-areas
===================

select-areas is a jQuery plugin that let you select multiple areas of an image,
move them and resize them.

It is used by :
 - [360learning](https://360learning.com)

# Quick Start

## Use like so:

    $("#mypic").selectAreas({
      minSize: [30, 30],    // Minimum size of a selection
      maxSize: [400, 300],  // Maximum size of a selection
      onChanged: $.noop,    // fired when a selection is released
      onChanging: $.noop    // fired during the modification of a selection
    });


## Want an example to learn from?
Check out example/example.html

# API Doc

## Area:
An area is described (when retrieved or set) by a json object :
    {
        id, // ID identifying the area in the plugin
        x,  // X coordinate (Position)
        y,  // Y coordinate (Position)
        z,  // Z-index (0 when inactive or 100 when focused)
        w,  // Width of the area
        h   // Height of the area
    }

## Options:
Here is a list of available options for selectAreas, with their default value:

 - allowEdit (true) : When set to false, unset allowMove, allowResize, allowSelect and allowDelete
 - allowMove (true) : When set to false, Areas can not be moved.
 - allowResize (true) : When set to false, Areas can not be resized.
 - allowSelect (true) : When set to false, Areas can not be created.
 - allowDelete (true) : When set to false, Areas can not be deleted.
 - aspectRatio (0) : When not 0, force a ratio between height and width for the selections.
 - minSize ([0, 0]) : When not 0, set minimum size for a selection [width, height]
 - maxSize ([0, 0]) : When not 0, set maximum size for a selection [width, height]
 - outlineOpacity (0.5) : opacity of the moving dotted outline around a selection.
 - overlayOpacity (0.5) : opacity of the overlay layer over the image
 - areas ([]) : list of areas to add to the image from the beginning  (id will be ignored)
 - onChanging (null) : triggered when the event "changing" is fired
 - onChanged (null) : triggered when the event "changed" is fired

## Events:
Two events are fired by the plugin :
 - changing : fired during the modification of a selection. arguments : (event, id, areas)
 - changed  : fired when a selection is released. arguments : (event, id, areas)

## Methods:
Once you added a *selectAreas* plugin on an image, Several method are exposed to help you
manipulate and retrieve these areas.
 - areas () : returns an array of areas
 - add (options) : add an area
 - remove (id) : remove an area with its id
 - reset () : remove all areas
 - destroy () : remove the *selectAreas* plugin
 - blurAll () : blur (unfocus) all the areas
 - contains (point) : return true or false whether or not a point ({x: X, y: Y}) is included in at least one area
