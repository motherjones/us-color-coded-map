# A Google Spreadsheet-Powered SVG Map

Build a US map with tooltips using data from a Google spreadsheet, complete with classes and info boxes. This works well for stories comparing states or tracking state-level legislation. Here's an example from the wild:

**screenshot here**

## Examples in the wild

[Map: Which States Allow Gay Marriage?](www.motherjones.com/politics/2014/05/gay-marriage-states-legal-map)

[Maps: Solitary Confinement, State by State](http://www.motherjones.com/politics/2012/10/map-solitary-confinement-states) 

[Has Your State Outlawed Blowing the Whistle on Factory Farm Abuses?](http://www.motherjones.com/blue-marble/2013/06/ag-gag-laws-map)

## How it works 


## Set up your Google Spreadsheet

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
    </div>
</div>

<link href="css/style.css" rel="stylesheet" />
<script src="libs/jquery.js"></script>
<script src="libs/tabletop.js"></script>	
<script src="js/map_snippet.js"></script>	
<script>
    super_simple_map({
      container: 'state_specific_area', //This should match  the id of the section up there
      initial_state: 'CA', //if you want to have a state initially selected
      //proxy: proxy here, //for a tabletop proxy, if you have one
      key: 'https://docs.google.com/spreadsheet/pub?key=0Aq7nL59nLsCMdDJxZUo4cFZaWGF5d0pSZU9XSE44NVE&output=html',
    })
</script>
```

If you are working in a new directory, make sure the jQuery and tabletop links are pointing to the correct location.

Et voila! You have a svg map hooked up to live data in a Google spreadsheet. When you make changes to the spreadsheet data, the map will automatically render those changes.

Now you can add some bells and whistles to the map and info boxes, such as color fills, hover states, and transitions.

## Style your Super Simple SVG Map

To color your state, open up the CSS file and make new classes based on the values in your Class column. Example:

.map_container .Legal {
	
	fill:#7fbf7b;
}


Since the states are svg paths, use "fill" instead of "background", and "stroke" instead of "border".

Beyond that, the important parts are :

* \#blurbHeadline : The headline that you pass in.

* \#state_specific_body : The body that you pass in.

* \#map_container path : all the states

* .clickable : Every state that has information attached to it.  Consider making the cursor a pointer for these.

* .selected : The state that was clicked on most recently, and the state who's headline and body you're currently displaying

## Staging the prettylist (for MoJo users)

*MoJo users:* When you're done, upload to s3 and embed in the shell [(follow this how to)](https://github.com/motherjones/story-tools#starting-a-new-project).

## Questions?

Hit us up by email, or Twitter: [@jaeahjlee](https://twitter.com/jaeahjlee) or [@tasneemraja](https://twitter.com/tasneemraja)

## Credits

[Ben Breedlove](http://twitter.com/bdbreedlove) built it.

[Jaeah Lee](http://twitter.com/jaeahjlee) added the bells and whistles.

[Tasneem Raja](http://twitter.com/tasneemraja), who headbangs to Fleetwood Mac _Rhiannon_ while writing documentation, edited it.

## License
Copyright (c) 2012 Mother Jones
