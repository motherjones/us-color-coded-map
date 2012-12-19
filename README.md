Super Simple SVG Map
===================

This is about as generalized and basic that I can make an implementation of an svg map setup that has classes and tooltips based on a google spreadsheet.

Ideally, this means that the only thing that our reporters need to make an interactive svg map is an understanding of css for svgs

TODO: write a css file so that our reporters don't need to know the basics of css for svgs.

HOW TO DO IT

Go in, change the spreadsheet id (currently "YOUR KEY GOES HERE!!!! !!! 111 one eleven") to your google spreadsheet id, and you should be good to go.

This assumes your spreadsheet has the following columns:

abbr : The abbreviation of the state you want to add a class or tooltip to

tooltipheadline : The headline of your tooltip for that state

tooltipbody : The body of your tooltip for that state

class : the class you'd like attached to your state, for styling


If you're at motherjones and you want to stage this, you'll have to remove the link to the jquery library so there aren't any collisions
