# Super Simple SVG Map

## Spreadsheets to Maps!

A simple way to make a svg map that displays data in a Google spreadsheet, complete with classes and info boxes. This enables anyone in our newsroom who knows spreadsheets and a tiny bit of CSS to whip up a sleek, interactive map, and make changes to it without a whole lot of heavy lifting on our part.

We've made a barebones version of the map available for download so you can [add styling](https://github.com/motherjones/super-simple-svg-map-from-spreadsheet#3-style-your-super-simple-svg-map) as desired. Here's an example of a Super Simple SVG Map with styling:

[Demo](http://motherjones.github.com/super-simple-svg-map-from-spreadsheet/)

## Getting started: 

### 1) Get your spreadsheet together

Start a new Google Spreadsheet with the following column headers:

    abbr   headline   body   class

The columns we care about are as follows:

* abbr : The abbreviation of the state you want to add a class or info box to (make sure your state column has abbreviated state names, not full names)

* headline : The headline of your info box for that state, displayed under the map

* body : The body of your info box for that state, displayed under the headline

* class : the class you'd like attached to your state, for styling

You can have other columns in there if you'd like. They won't show up in the map, but they won't break it either.

In Google Docs, go up to the `File` menu and pick `Publish to the web`. Before publishing your map, double check that you are publishing the correct sheet in the "Sheets to Publish" drop down menu. Make sure there is only one worksheet powering your map. 

Click `Start publishing`. A URL will appear, something like `https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdG5GWHFXbWJlN1hTR2ZmN3lZMVZkOHc&output=html`

Copy the part between `key=` and `&`. This is your spreadsheet key.

In the code snippet below, change the spreadsheet id (currently "YOUR KEY GOES HERE") to your Google spreadsheet key.

[Demo spreadsheet](https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc&output=html)

### 2) Set up your html page

If you're working locally and inside the super simple svg repo's directory, you can just paste the below code snippet into your web page, and replace 'YOUR KEY GOES HERE' with your spreadsheet key.

```
<div id="map_container">
    <div id="state_specific_area">
        <h1 id="state_specific_headline">Headline here will be automatically replaced w/ info box title</h1>
        <p id="state_specific_body">Paragraph here will be automatically replaced w/ info box text</p>
    </div>
</div>

<link href="css/style.css" rel="stylesheet" />
<script src="libs/jquery.js"></script>
<script src="libs/tabletop.js"></script>	
<script src="js/map_snippet.js"></script>	
<script>
    Tabletop.init({ 
        key: "YOUR KEY GOES HERE",
        callback: function(data) {
			color_map(data);
			place_state_specific_data(data);
        },
        simpleSheet: true
    });
</script>
```

If you are working in a new directory, make sure the jQuery and tabletop links are pointing to the correct location.

Et voila! You have a svg map hooked up to live data in a Google spreadsheet. When you make changes to the spreadsheet data, the map will automatically render those changes. Neat, huh? 

Now you can add some bells and whistles to the map and info boxes, such as color fills, hover states, and transitions.

### 3) Style your Super Simple SVG Map

The exciting part, of course is going to be the classes you add. 

To color your state shapes, open up the CSS file and make new classes based on the values in your Class column. Example:

.map_container .Legal {
	
	fill:#7fbf7b;
}


REMEMBER: Since the states are svg paths, use "fill" instead of "background", and "stroke" instead of "border".

Beyond that, the important parts are :

* \#state_specific_headline : The headline that you pass in.

* \#state_specific_body : The body that you pass in.

* \#map_container path : all the states

* .clickable : Every state that has information attached to it.  Consider making the cursor a pointer for these.

* .selected : The state that was clicked on most recently, and the state who's headline and body you're currently displaying


## Super Simple SVG Map in the wild

A [series of maps documenting](http://www.motherjones.com/politics/2012/10/map-solitary-confinement-states) solitary confinement laws in the US by state, with info boxes and style.

A [map](http://www.motherjones.com/blue-marble/2013/06/ag-gag-laws-map) showing states where it's becoming more difficult for activists and journalists to investigate and report animal abuses.


## Credits

[Ben Breedlove](http://twitter.com/bdbreedlove) built it.

[Jaeah Lee](http://twitter.com/jaeahjlee) added the [bells and whistles](https://github.com/motherjones/super-simple-svg-map-from-spreadsheet#3-style-your-super-simple-svg-map).

[Tasneem Raja](http://twitter.com/tasneemraja), who headbangs to Fleetwood Mac _Rhiannon_ while writing documentation, edited it.
