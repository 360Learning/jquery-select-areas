jQuery-select-areas
===================

jQuery-select-areas is a jQuery plugin that let you select multiple areas of an image,
move them and resize them.

It is used by:
 - [360learning](https://360learning.com)

![jQuery-select-areas Preview](https://rawgit.com/360Learning/jquery-select-areas/master/jQuerySelectAreas-Preview.png)

# Project continuation

We (360Learning) no longer have the time to maintain this project, so the issue tracker has been closed. If someone wants to get admin access to this repository to fix the few bugs that are reported, we would gladly agree. Else, there already are some forks of this project, so don't hesitate to use them if they have fixed a bug that is bother you.
Best regards

# Quick Start

## Use like so:

    $("#mypic").selectAreas({
      minSize: [30, 30],    // Minimum size of a selection
      maxSize: [400, 300],  // Maximum size of a selection
      onChanged: $.noop,    // fired when a selection is released
      onChanging: $.noop    // fired during the modification of a selection
    });


## Want an example to learn from?
Check out [example/example.html](https://rawgit.com/360Learning/jquery-select-areas/master/example/example.html)

## Browser Compatibiilty:
This plugin is fully compatible with every modern browser and IE >= 9.

One of the features : scaling image, in order to display it smaller or bigger than it actually is, is not compatible with IE8.
If you need to use this feature and to maintain a compatibility with IE8, you can add the alternate stylesheet *resources/jquery.selectareas.ie8.css*.
This will make it work but uglify the whole plugin. This stylesheet can be added for IE8 only with conditional comments (see *example/example.html*).

# API Doc

## Area
An area is described (when retrieved or set) by a json object:

    {
        id, // ID identifying the area in the plugin
        x,  // X coordinate (Position)
        y,  // Y coordinate (Position)
        z,  // Z-index (0 when inactive or 100 when focused)
        width,  // Width of the area (Size)
        height  // Height of the area (Size)
    }

## Options
Here is a list of available options for selectAreas, with their *default value*:

 - **allowEdit** (*true*) : When set to false, unset allowMove, allowResize, allowSelect and allowDelete
 - **allowMove** (*true*) : When set to false, Areas can not be moved with a drag & drop.
 - **allowResize** (*true*) : When set to false, Areas can not be resized.
 - **allowSelect** (*true*) : When set to false, Areas can not be created.
 - **allowDelete** (*true*) : When set to false, Areas can not be deleted.
 - **allowNudge** (*true*) : When set to false, Areas can not be moved with arrow keys.
 - **aspectRatio** (*0*) : When not 0, force a ratio between height and width for the selections.
 - **minSize** (*[0, 0]*) : When not 0, set the minimum size for a selection [width, height]
 - **maxSize** (*[0, 0]*) : When not 0, set the maximum size for a selection [width, height]
 - **maxAreas** (*0*) : When not 0, set the maximum number of area that can be drawn.
 - **outlineOpacity** (*0.5*) : opacity of the moving dotted outline around a selection.
 - **overlayOpacity** (*0.5*) : opacity of the overlay layer over the image
 - **areas** (*[]*) : list of areas to add to the image from the beginning  (id will be ignored)
 - **onChanging** (*null*) : triggered when the event "changing" is fired
 - **onChanged** (*null*) : triggered when the event "changed" is fired
 - **onLoaded** (*null*) : triggered when the event "loaded" is fired
 - **width** (*0*) : When not 0, scale the image to this width (px). The coordinates of the areas on the full image can be retrieved with method relativeAreas()

## Events
Three events are fired by the plugin:
 - **loaded** : fired when plugin is loaded
 - **changing** : fired during the modification of a selection. arguments : (event, id, areas)
 - **changed**  : fired when a selection is released. arguments : (event, id, areas)

## Methods
Once you added a *selectAreas* plugin on an image, several method are exposed to help you
manipulate and retrieve these areas:
 - **areas ()** : returns an array of areas
 - **relativeAreas ()** : returns an array of areas, with their size and coordinates on the original image (see option width). Equal to areas() when the image is displayed in full size.
 - **add (options)** : add an area
 - **remove (id)** : remove an area with its id
 - **reset ()** : remove all areas
 - **destroy ()** : remove the *selectAreas* plugin
 - **blurAll ()** : blur (unfocus) all the areas
 - **contains (point)** : return true or false whether or not a point ({x: X, y: Y}) is included in at least one area
