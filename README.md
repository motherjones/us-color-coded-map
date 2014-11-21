# A Google Spreadsheet-Powered SVG Map

Build a US map with tooltips using data from a Google spreadsheet, complete with classes and info boxes. This works well for stories comparing states or tracking state-level legislation. Here's an example from the wild:

<p align="center">
  <img width="75%" src="https://github.com/motherjones/us-tooltip-map/blob/master/img/screenshot.png" alt="screenshot"/>
</p>

## Examples in the wild

[Map: Which States Allow Gay Marriage?](www.motherjones.com/politics/2014/05/gay-marriage-states-legal-map)

[Maps: Solitary Confinement, State by State](http://www.motherjones.com/politics/2012/10/map-solitary-confinement-states) 

[Has Your State Outlawed Blowing the Whistle on Factory Farm Abuses?](http://www.motherjones.com/blue-marble/2013/06/ag-gag-laws-map)

## How it works 

*MoJo users:* Before you get started, follow [these instructions](https://github.com/motherjones/story-tools#starting-a-new-project).

This map consists of a title, deck, legend, source line, svg map, and a tooltip view. You'll customize all elements in the index.html file, except for the svg map and tooltip, which you'll customize through the Google Spreadsheet. We'll get into details below, but in brief, you'll follow these simple steps:

* Start with a spreadsheet with the following column headers:

|**abbr**|**headline**|**body**|**class**|
|---|----|-----|----|
|  |    |     |    |

* Add details about the states you're mapping in each row:

|**abbr**|**headline**|**body**|**class**|
|---|----|-----|----|
|KS|Kansas|Voters approved a constitutional ban on same-sex marriage in 2005. It was already illegal under state law. A 2012 statute reiterated the state's ban on same-sex marriages. A lawsuit was filed in 2013 seeking state acknowledgement of out-of-state marriages for tax purposes. On November 4, 2014, a federal judge issued a prelimnary injuction against the enforcement of the state's ban. However, that injuction was stayed to allow Kansas time to appeal.|Limbo|

* Customize the other elements of the map container by editing parts of your index.html file:
```
<div class="container-fluid">  
    <h2>Where is Gay Marriage Legal in the US?</h2>
    <p>The most recent status of gay marriage, across the US. Latest state to legalize highlighted below. Click any state for details.</p>
    <ul class="list-inline">
        <li><span class="Legal">tag</span> Legal</li>
        <li><span class="Appeal">tag</span> Ban struck down, appeal pending</li>
        <li><span class="Challenged">tag</span> Banned, currently challenged in court</li>
        <li><span class="Banned">tag</span> Banned</li>
    </ul>
    <aside class="small text-muted">Source: Lambda Legal, Human Rights Campaign</aside>
    <section id="blurb"></section>  
</div>

<script src="js/jquery.js"></script>
<script src="js/tabletop.js"></script>	
<script type="text/javascript" src="http://assets.motherjones.com/interactives/plugins/pym.js/src/pym.js"></script>
<script src="js/script.js"></script>	
<script>
    us_map ({
      container: 'blurb',
      initial_state: 'CA',
      //proxy: proxy here,
      key: 'https://docs.google.com/spreadsheet/pub?key=0Aq7nL59nLsCMdDJxZUo4cFZaWGF5d0pSZU9XSE44NVE&output=html',
    })
</script>
```

* Style the container to fit your data's story by editing parts of your style.css file:
```
/*  project-specific styles for map and legend */
.Legal {	
	fill:#69A9C5;
    background:#69A9C5;
    color: #69A9C5;
}
.Appeal {   
    fill:#ABD9E9;
    background:#ABD9E9;
    color:#ABD9E9;
}
.Challenged {
	fill: #F4A582;
    background:#F4A582;
    color:#F4A582;
}
.Banned { 
    fill:#D6604D;
    background:#D6604D;
    color:#D6604D;
}
```

## Set up your Google Spreadsheet
 
Make a copy of [this template](https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc&output=html) and move the copy into the relevant beat folder in the Mother Jones Google Drive. Rename the spreadsheet as you see fit. Change the owner of the spreadsheet to MoJo Data in `Share > Advanced`.

In order for the map to be able to read your spreadsheet, you'll need to make your new spreadsheet public. Go to `File` and click on `Publish to the web,` then click on `Start publishing`. 

A URL will appear. It will look something like this: 

```
https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdHc4MDVLcEl6bHFhczNKSzZUem1VYWc&output=html
```

Copy that link. This is your spreadsheet ID or url, which you will use to connect your spreadsheet to the map.

## Formatting your spreadsheet data

* `abbr` : The abbreviation of the state you want to add a class or info box to (make sure your state column has abbreviated state names, not full names)

* `headline` : The headline of your info box for that state, displayed under the map

* `body` : The details for that state, displayed under the headline. (**Pro tip:** Keep the body word count consistent across all states.)

* `class` : Single words that categorize each state, which will determine the color of each state shape and the boxes in the legend. In the demo, we have four categories under `class`: legal, appeal, challenged, banned. These classes 

It's best to keep your spreadsheet clean and limited to these four columns, but if you need, feel free to add additional columns for reference (sources for each row's data, and so on). They won't show up in the map, but they won't break it either.

## Modify your project files

*MoJo users:* By now you should have a local copy of this project repository on your machine. If you don't, go back and follow [these instructions](https://github.com/motherjones/story-tools#starting-a-new-project).

**In your copy of index.html:**

In order to get your data showing up in the map, you'll need to edit a couple of lines of code in your index.html file. 

* Paste the ID or url you just copied from your spreadsheet, and paste it in the place of `your_spreadsheet_url_here`. The code you are looking for in the index.html file looks like this:

```
<script>
    us_map ({
      container: 'blurb',
      initial_state: 'CA',
      //proxy: proxy here,
      key: 'your_spreadsheet_url_here',
    })
</script>
```
* Next, replace the headline, deck, and legend with your story content. This is the code you're looking for:
```
    <h2>Where is Gay Marriage Legal in the US?</h2>
    <p>The most recent status of gay marriage, across the US. Latest state to legalize highlighted below. Click any state for details.</p>

    <ul class="list-inline">
        <li><span class="Legal">tag</span> Legal</li>
        <li><span class="Appeal">tag</span> Ban struck down, appeal pending</li>
        <li><span class="Challenged">tag</span> Banned, currently challenged in court</li>
        <li><span class="Banned">tag</span> Banned</li>
    </ul>

    <aside class="small text-muted">Source: Lambda Legal, Human Rights Campaign</aside>
    
    <section id="blurb"></section>  
```
Save your changes. Open up index.html using a web browser and check that your data is showing up in the map container. When you make changes to the spreadsheet data, the map will automatically render those changes.

**In your copy of style.css:**

Make sure the categories you added to the `class` column matches the .classes in your style.css file. `fill`, `background`, and `color` are CSS properties that assign each class its own color. Each of these properties should have a hex code (e.g. #69A9C5) that denotes the corresponding color for that class. If you've added more than four categories, make sure you add them here as well, along with their `fill`, `background`, and `color`.

```
/*  project-specific styles for map and legend */
.Legal {	
	fill:#69A9C5;
    background:#69A9C5;
    color: #69A9C5;
}
.Appeal {   
    fill:#ABD9E9;
    background:#ABD9E9;
    color:#ABD9E9;
}
.Challenged {
	fill: #F4A582;
    background:#F4A582;
    color:#F4A582;
}
.Banned { 
    fill:#D6604D;
    background:#D6604D;
    color:#D6604D;
}
```
**Important note about CSS for <svg>s:** Since the state shapes are formed by svg paths, the CSS properties you'll need to use are "fill" instead of "background", and "stroke" instead of "border."

Refresh index.html in the web browser and check that your data is still showing up in the map, colored properly, and has the new headline/deck/source.

## Stage the map (for MoJo users)

*MoJo users:* When you're done, upload to s3 and embed in the shell [(follow this how to)](https://github.com/motherjones/story-tools#starting-a-new-project).

## Questions?

Hit us up by email, or Twitter: [@jaeahjlee](https://twitter.com/jaeahjlee) or [@tasneemraja](https://twitter.com/tasneemraja)

## Credits

[Ben Breedlove](http://twitter.com/bdbreedlove) built it.

[Jaeah Lee](http://twitter.com/jaeahjlee) added the bells and whistles.

[Tasneem Raja](http://twitter.com/tasneemraja), who headbangs to Fleetwood Mac _Rhiannon_ while writing documentation, edited it.

## License
Copyright (c) 2012 Mother Jones
