<img src="images/zoom.png" width="50">

*Note that this session will be recorded.*
## Set up

### Copy the GitHub repo clone link

In your GitHub repo page, copy the clone link:

<img src="images/clone.png">

### Set up VSCode

Open VS Code

In your Welcome window, (1) click on the `source control` menu icon on the left, (2) click on `clone repository`, and (3) enter your repo url in the text box.

<kdb><img src="images/vsclone.png"></kbd>

You will be asked to choose a location on your hard drive to save the files. If you are prompted to open the repository, do so.

## Create your first html page

1. Click on `New file` icon
1. Enter `index.html` as the file name

<kbd><img src="images/vs_index.png"></kbd>

The file should popup as an empty tab on the right. Enter (copy and paste) the following code:

```html
<!DOCTYPE html>
<html>
<head>
	<title>Hello World</title>
	<meta charset="utf-8" />

	<!-- style sheets -->
	<link rel="stylesheet" href="css/style.css">

</head>
<body>

	<div class="header">
		Hello World
	</div>
	<div class="sidebar">
		My Sidebar
	</div>
	<div class="content">
		My Map
	</div>

</body>
</html>
```

> What do you observe in the code? 
> 1. Define the three top level elements
> 2. How do you write comments in HTML?
> 3. What do you think is a stylesheet?
> 4. What are classes?

Save the file and open it in chrome. Hint: right click on your `index.html` file and `reveal in file explorer`. Then, double click on the file.

> What do you see in the browser?
> 1. What happens if you change the "Hello World" text to something else?
> 1. Where did your sidebar and content go?

Open the Developer tools as shown below (or Ctrl+Shift+I)

<kbd><img src="images/developertools.png"></kbd>

Click on the `console` tab

> What do you see in the console?
> How may you fix the error?

## Create a css stylesheet file

As noted, the html code assumes you have a css file.

1. Click on the create new folder button
1. Name the folder `css`
1. Inside the `css` folder, create a new file named `style.css`

<img src="images/stylecss.png">

Enter the following code:

```css
body,html {
	margin:0;
	height:100%;
	width:100%;
}

#map {
	height: 100%;
}

body {
    display: grid;
	grid-template-rows: 80px 1fr;
	grid-template-columns: 250px 1fr;
	grid-template-areas: 
	"header header"
	"sidebar content";
}

.header {
	grid-area: header;
	padding:10px;
    background-color: #333;
}
.sidebar {
	grid-area: sidebar;
	padding:10px;
    background-color: #555;
}
.content {
	grid-area: content;
}
```

Save the file, and refresh your browser page that has `index.html`

> How did the css file affect the page?
> 1. The text in your header is now black on a dark background. Change the text color to white (hint: use `font-color`)
> 1. Choose colors of your liking, and modify the `background-color` values for your `header` and `sidebar`
> 1. Modify the `font-color` appropriately so that there is enough contrast between the text color and the background color.

## Map time!

Now it is time to add a map to our html page. This is a multi-step process that entails the following:

1. Bring the leaflet javascript library into the html page
1. Bring the leaflet css into the html page
1. Add a `<div>` to put the map in
1. Add leaflet code to create the map

Take a moment to observe the [leaflet](https://leafletjs.com) website.

### Part 1: Bring in leaflet
We can bring the leaflet javascript and css libraries into our html page using a [cdn](https://leafletjs.com/download.html)

Put the following code in the `<head>` area of your `index.html` file.

```html
<!-- leaflet -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
```
> Did you remember to indent your code? Unlike, say, Python, html indentation is not required, but it is always a good idea to keep your code "clean" by following indentation standards throughout your code

### Part 2: Create a map div

Replace the "My Map" text in your `content` div with the following:

```html
<div id="map"></div>
```

### Part 3: Javascript time

Now we are finally ready to create our interactive web map. Remember that interactive web development uses Javascript, so we first need to create a space in our html page that allows us to write javascript code.

Inside the `<body></body>` tags, and right after that last closing `</div>` tag, enter the following:

```html
<script>
	alert('hello javascript alert!')
	console.log('hello console!')
</script>
```

> Save the file, and refresh the page in your browser. 
> 1. What happens?
> 1. Open your developer tools/console window. Do you see your message?

### Part 4: Leaflet javascript

Delete the alert and console lines. Add the following leaflet "starter" code inside the `<script></script>` tags:

```javascript
var map = L.map('map').setView([34.0697,-118.4432], 17);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
	attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

var marker = L.marker([34.0697,-118.4432]).addTo(map)
		.bindPopup('The Technology Sandbox<br> Where Yoh is sitting this very moment')
		.openPopup();	
```

> ### Make it your own
> Now that you have command over your maproom, modify it and make it your own. Try:
> 1. Change the map marker location to a place of your interest
> 1. Add relevant content in the header and sidebar sections
> 1. Change the colors in the stylesheet, and if you are adventurous, change other stylesheet parameters
> 1. Add more markers to the map, with appropriate popup content

### Push your new files to your GitHub repo

Now that you are satisfied with your _local_ version of your maproom, it is time to add it to your GitHub repo. This will allow you to publish your map to the world!

VS Code comes replete with GitHub features. Let's take full advantage of them. 

1. Click on the `Source Control` tab, check that you have files that have been added/modified, and then
1. add a message text for your commit, and
1. commit your changes by clicking on the checkbox icon.

<kbd><img src="images/vs_commit.png"></kbd>

There is one step left. You have just commited your changes to your _local_ repo. You need to **push** your changes to your _online_ GitHub repo. 

1. Click on the "more actions" button (triple dot)
1. Click on `Push`

<kbd><img src="images/vs_push.png"></kbd>

## View your website

Assuming you have GitHub pages enabled, you should now be able to see your website with a public URL. Change the url to match your own GitHub pages url.

*Note that it may take a minute or two after you commit your files for them to be available on GitHub pages.*

<img src="images/firstmap.png">

### Bonus: Using the Terminal to push

If you prefer to use the terminal to do your git commands (instead of the GUI interface provided by VS Code), then the following commands will push your changes to your repository.

1. In VS Code's menu bar, go to `Terminal`, `New Terminal`
1. Check that you are in the right place:
	```PowerShell
	git status
	```
1. Add modified/new files to your staging area:
	```PowerShell
	git add .
	```
1. Commit your files with a message:
	```PowerShell
	git commit -m "maproom changes"
	```
1. Push your changes to your repo:
	```PowerShell
	git push
	```

## Part 2: Javascript basics


In your Chrome browser, you should now see your index.html file with a fully interactive leaflet map.

When loading a web page which is associated with one or more scripts, the JavaScript code is automatically interpreted and executed by the browser. We can also manually interact with the browser’s interpreter or engine using the JavaScript console, also known as the command line, which is built into all modern web browsers. The console is basically a way to type code into a computer and get the computer’s answer back. This is useful for experimenting with JavaScript code, such as quickly testing short JavaScript code snippets. It is exactly what we are going to do.

## Developer's tools

Open the developer's tools (ctrl-shift-i) and select the console tab.

Enter the following javascript code (feel free to change the message):

```js
alert('I love Javascript')
```
<kbd><img src="images/console.png"></kbd>

How about some math:

```js
1 + 1
```

>Experiment with other arithmetic features. What can and can it not do?

### Variables

Variables can be declared in three ways.

```js
var d1 = "I am a var variable, and I am old school";
let d2 = "I am a let variable, the new and cool way to define variables";
const d3 = "I am a const variable, and you can't change me";
```


### Data types

#### Strings: Single or double quotes

```js
let s1 = 'Mapping' // I am a string
let s2 = 'is fun' // I am also a string
```

Concatenation

```js
s1 + s2
```

> This results in `Mappingis fun`. How do you fix the sentence?


Adding to existing strings
```js
html = '<h1>My Map</h1>'
html += '<ul>'
html += '<li>Osaka</li>'
html += '<li>Bangkok</li>'
html += '<li>Tokyo</li>'
html += '<li>Los Angeles</li>'
html += '</ul>'
```

#### Numbers

```js
let x = 10;
let y = 3;
```
Variables can do math too!
```js
x*y
```

> Question: What happens when you add a string to a number? (ex. `s1 + x`)


#### Arrays: Square brackets `[]`

```js
let cities = ['Osaka','Bangkok','Tokyo','Los Angeles']
```
How many values (length)?
```js
cities.length
```
Getting specific array values. Note that array count begins with "0" and not "1"
```js
cities[0]
cities[1]
cities[2]
cities[3]
```
#### Objects: Squiggly brackets `{}`
A javascript object is a great way to store a collection of data in `key:value` pairs.

```js
let city = {
	'title':'Hello Osaka',
	'lat': 34.6937,
	'lon': 135.5023
};
```

Grab "values" by requesting its key:

```js
city.title
```


#### Objects in Arrays
By putting objects with identical key:value pairs, we can begin to construct a data table.
```js
let data = [
	{
		'title':'Osaka',
		'lat': 34.6937,
		'lon': 135.5023
	},
	{
		'title':'Cali',
		'lat': 3.4516,
		'lon': -76.5320
	},
	{
		'title':'Bangkok',
		'lat': 13.7563,
		'lon': 100.5018
	},
	{
		'title':'Tokyo',
		'lat': 35.6762,
		'lon': 139.6503
	},
	{
		'title':'LA',
		'lat': 34.0522,
		'lon': -118.2437
	}
]
```

Challenge questions:
1. How do you get specific array objects?
1. Get the latitude coordinate for Tokyo using javascript code

### Loops

Looping allows you to *iterate* through an array.

Loop through an array:

```js
// loop through cities
cities.forEach(function(item){
	console.log(item)
});
```

Loop through an array of objects:
```js
// loop through data
data.forEach(function(item){
	console.log(item)
});
```

You can choose to return *specific* elements from each data object.

```js
// loop through data
data.forEach(function(item){
	console.log('The latitude for ' + item.title + ' is ' + item.lat)
});
```
Challenge exercise:
1. Add a `description` key to the data array objects, and enter a sentence per city.
1. Loop through each data object, and create the following statement for each city: 

`The coordinates for _city_ are _lat_, _lon_. _City_ is _description_.`

## In-class Exercise (time permitting)

Now it is your turn to put all this newfound javascript knowledge into practice.

1. In your `index.html` file, and in the javascript section of your code (`<script></script>`), create an array of objects that lists locations that you have travelled to (include at least 5 locations). Make sure to include a title, description, latitude, and longitude for each.
1. Replace the code that generates the single marker with a loop that goes through your array of objects. Then, create a marker for each location. Make sure to include a title and description in the popup.
1. Add a title of your maproom in the header section.
1. Add a title and description of your map in the sidebar section.
1. When you are done, upload your additions to your GitHub Repo 

**Bonus**: Add an image for each city in your narrative.
