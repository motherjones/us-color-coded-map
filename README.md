# Super Simple SVG Map

This is about as generalized and basic that I can make an implementation of an svg map setup that has classes and tooltips based on a google spreadsheet.

Ideally, this means that the only thing that our reporters need to make an interactive svg map is an understanding of css for svgs

###To Do: 

Write a css file so that our reporters don't need to know the basics of css for svgs.

# How to do it :

### 1) Get your spreadsheet together

Start a new Google Spreadsheet with the following column headers:

    abbr     tooltip headline   tooltip body   class

The columns we care about are as follows:

* abbr : The abbreviation of the state you want to add a class or tooltip to

* tooltipheadline : The headline of your tooltip for that state

* tooltipbody : The body of your tooltip for that state

* class : the class you'd like attached to your state, for styling

You can have other columns in there if you'd like, but they're not gonna do anything.

In Google Docs, go up to the `File` menu and pick `Publish to the web`. Fiddle with whatever you want, then click `Start publishing`. A URL will appear, something like `https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdG5GWHFXbWJlN1hTR2ZmN3lZMVZkOHc&output=html`

Copy that! In theory you're interested in the part between `key=` and `&` but you can use the whole thing if you want.

[Demo spreadsheet](https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc&output=html)

### 2) Set up your html page

If you're in the super simple svg repo's directory, you can just paste this somewhere, and replace `YOUR KEY GOES HERE!!!! !!! 111 one eleven` with your spreadsheet url.

```
<div id="map_container">
    <div id="tooltip_area">
        <h1 id="tooltip_headline">Headline here will be automagically replaced w/ tooltip title</h1>
        <p id="tooltip_body">Paragraph here will be automagically replaced w/ tooltip text</p>
    </div>
</div>

<link href="css/style.css" rel="stylesheet" />
<script src="libs/jquery.js"></script>
<script src="libs/tabletop.js"></script>	
<script src="js/map_snippet.js"></script>	
<script>
    Tabletop.init({ 
        key: "YOUR KEY GOES HERE!!!! !!! 111 one eleven",
        callback: function(data) {
			color_map(data);
			place_tooltips(data);
        },
        simpleSheet: true
    });
</script>
```

If you want to put this somewhere for real though, you'll have to replace jQuery and tabletop links with links to point to their new home, and maybe write your own css.

### 3) Style it

The exciting part, of course is going to be the classes you add. Remember that since the states are svg paths, you use "fill" instead of "background", and "stroke" instead of "border".

Beyond that, the important parts are :

* \#tooltipheadline : The headline that you pass in.

* \#tooltipbody : The body that you pass in.

* \#map_container path : all the states

* .clickable : Every state that has information attached to it.  Consider making the cursor a pointer for these.

* .selected : The state that was clicked on most recently, and the state who's headline and body you're currently displaying
