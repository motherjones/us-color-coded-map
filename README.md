# Super Simple SVG Map

## Spreadsheets to Maps!

A simple way to make a svg map that displays data in a Google spreadsheet, complete with classes and tooltips. This enables anyone in our newsroom who knows spreadsheets and a tiny bit of CSS to whip up a sleek, interactive map, and make changes to it without a whole lot of heavy lifting on our part.

Here's what it looks like:

[Demo]()

## Getting started: 

### 1) Get your spreadsheet together

Start a new Google Spreadsheet with the following column headers:

    abbr     tooltip headline   tooltip body   class

The columns we care about are as follows:

* abbr : The abbreviation of the state you want to add a class or tooltip to

* tooltipheadline : The headline of your tooltip for that state

* tooltipbody : The body of your tooltip for that state

* class : the class you'd like attached to your state, for styling

You can have other columns in there if you'd like. They won't show up in the map, but they won't break it either.

In Google Docs, go up to the `File` menu and pick `Publish to the web`. Fiddle with whatever you want, then click `Start publishing`. A URL will appear, something like `https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdG5GWHFXbWJlN1hTR2ZmN3lZMVZkOHc&output=html`

Copy that! In theory you're interested in the part between `key=` and `&` but you can use the whole thing if you want.

Go in, change the spreadsheet id (currently "YOUR KEY GOES HERE!!!! !!! 111 one eleven") to your google spreadsheet id, and you should be good to go.

[Demo spreadsheet](https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc&output=html)

### 2) Set up your html page

If you're working locally and inside the super simple svg repo's directory, you can just paste the below code snippet into your web page, and replace `YOUR KEY GOES HERE!!!! !!! 111 one eleven` with your spreadsheet url.

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

If you are working in a new directory, make sure the jQuery and tabletop links are pointing to the correct location.

Et voila! You have a svg map hooked up to live data in a Google spreadsheet. When you make changes to the spreadsheet data, the map will automatically render those changes. Neat, huh? 

Now you can add some bells and whistles, like color, tooltips, hover states, transitions.

### 3) Style your Super Simple SVG Map

The exciting part, of course is going to be the classes you add. 

REMEMBER: Since the states are svg paths, use "fill" instead of "background", and "stroke" instead of "border".

Beyond that, the important parts are :

* \#tooltipheadline : The headline that you pass in.

* \#tooltipbody : The body that you pass in.

* \#map_container path : all the states

* .clickable : Every state that has information attached to it.  Consider making the cursor a pointer for these.

* .selected : The state that was clicked on most recently, and the state who's headline and body you're currently displaying


## Super Simple SVG Map in the wild

A [series of maps documenting](http://www.motherjones.com/politics/2012/10/map-solitary-confinement-states) solitary confinement laws in the US by state, with tooltips and style.


## Credits

[Ben Breedlove](http://twitter.com/bdbreedlove) built it.

[Jaeah Lee](http://twitter.com/jaeahjlee) added the [bells and whistles]().

[Tasneem Raja](http://twitter.com/tasneemraja), who headbangs to Fleetwood Mac _Rhiannon_ while writing documentation, edited it.
