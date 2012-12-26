Super Simple SVG Map
===================

This is about as generalized and basic that I can make an implementation of an svg map setup that has classes and tooltips based on a google spreadsheet.

Ideally, this means that the only thing that our reporters need to make an interactive svg map is an understanding of css for svgs

## To Do: 

Write a css file so that our reporters don't need to know the basics of css for svgs.

## Getting Started

Go in, change the spreadsheet id (currently "YOUR KEY GOES HERE!!!! !!! 111 one eleven") to your google spreadsheet id, and you should be good to go.

Make sure your spreadsheet is published.

This assumes your spreadsheet has the following columns:

* abbr : The abbreviation of the state you want to add a class or tooltip to

* tooltipheadline : The headline of your tooltip for that state

* tooltipbody : The body of your tooltip for that state

* class : the class you'd like attached to your state, for styling

## Styling tips

The exciting part, of course is going to be the classes you add. Remember that since it's an svg, that you use "fill" instead of "background"

Beyond that, the important parts are :

* #tooltipheadline : The headline that you pass in.

* #tooltipbody : The body that you pass in.

* #map_container path : all the states

* .clickable : Every state that has information attached to it.  Consider making the cursor a pointer for these.

* .selected : The state that was clicked on most recently, and the state who's headline and body you're currently displaying
