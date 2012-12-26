Super Simple SVG Map
===================

This is about as generalized and basic that I can make an implementation of an svg map setup that has classes and tooltips based on a google spreadsheet.

Ideally, this means that the only thing that our reporters need to make an interactive svg map is an understanding of css for svgs

## To Do: 

Write a css file so that our reporters don't need to know the basics of css for svgs.

How to do it :
===================

## Get your spreadsheet together

Make sure your spreadsheet is published. In Google Docs go up to the `File` menu and pick `Publish to the web`.

The columns we care about are as follows:

* abbr : The abbreviation of the state you want to add a class or tooltip to

* tooltipheadline : The headline of your tooltip for that state

* tooltipbody : The body of your tooltip for that state

* class : the class you'd like attached to your state, for styling

You can have other columns in there if you'd like, but they're not gonna do anything.

## Stage it!

Find your google spreadsheet's key. Check out the url at the top of the browser when you're looking at your google spreadsheet. It should look something like `https://docs.google.com/spreadsheet/ccc?key=0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc#gid=0` The important part is between the `key=` and the `#gid=`

This part is your spreadsheet's key. 
`https://docs.google.com/spreadsheet/ccc?key=<em>0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc</em>#gid=0`

Go in, change the spreadsheet id (currently "YOUR KEY GOES HERE!!!! !!! 111 one eleven") to your google spreadsheet id, and you should be good to go, locally at least.

Really though, before you put this somewhere, you should probably place jQuery and tabletop somewhere and change the links to point to their new home, and maybe write your own css.

## Styling tips

The exciting part, of course is going to be the classes you add. Remember that since it's an svg, that you use "fill" instead of "background", and "stroke" instead of "border".

Beyond that, the important parts are :

* \#tooltipheadline : The headline that you pass in.

* \#tooltipbody : The body that you pass in.

* \#map_container path : all the states

* .clickable : Every state that has information attached to it.  Consider making the cursor a pointer for these.

* .selected : The state that was clicked on most recently, and the state who's headline and body you're currently displaying
