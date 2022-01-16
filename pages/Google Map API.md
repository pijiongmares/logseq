- #Dev-Notes #Javascript
- Description : Google Map API notes
-
- ## Setting Up The Map
	- Create project and billing in Google Cloud API
	- Create an API key in the Google Cloud API for the the Google Map
	- Setup Javascript for loading simple map
	- ```html
	  	<!DOCTYPE html>
	  	<html lang="en">
	  <head>
	  	 <meta charset="UTF-8">
	  	 <meta http-equiv="X-UA-Compatible" content="IE=edge">
	  	 <meta name="viewport" content="width=device-width, initial-scale=1.0">
	  	 <title>Google Map API</title>
	  </head>
	  <body>
	  	 <div id="map"></div>
	  	 <script src="map.js"></script>
	  </body>
	  	</html>
	  ```
	- map.js file (overkill setting the Javascript source)
	- ``` js
	  	var script = document.createElement("script");
	  	script.src ="https://maps.googleapis.com/maps/api/jskey=AIzaSyCRZLcvuJjXfC1FDN54vJhRm30asFrpBvk&callback=initMap";
	  	script.async = true;
	  
	  	window.initMap = function () {
	   new google.maps.Map(document.getElementById("map"), {
	  	center: { lat: -34.397, lng: 150.644 },
	  	zoom: 8,
	   });
	  	};
	  
	  	document.head.appendChild(script);
	  ```
	- Use new google.maps.Map(\<html element to place the map\>, \<options\>) to initialize the map
	- Center : longitude and latitude to focus
	- Zoom : zoom level (1: world, 5: landmass continent, 10: city, 15: street, 20: buildings)
- ## Markers
	- Set the marker/pin in the map
	- Position: longitude and latitude to mark
	- Map: map object
	- Icon: custom icon
	- ``` js
	  	let marker = new google.maps.Marker({
	  position: { lat: -34.397, lng: 150.644 },
	  map: map,
	  	});
	  ```
- ## infowindow
	- Displays a custom HTML popup overlay
	- Content: html element
	- ``` js
	  	let infoWindow = new google.maps.InfoWindow({
	  content: '<h1>Test</h1>',
	  	});
	  	marker.addListener('click', function(){
	  infoWindow.open(map, marker);
	  	})
	  ```
- ## places.searchbox
	- ``` js
	  	const input = document.getElementById("searchbox");
	  	const searchBox = new google.maps.places.SearchBox(input);
	  ```