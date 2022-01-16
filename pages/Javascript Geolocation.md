- #Dev-Notes #Javascript
- Description : Javascript Geolocation notes
-
- ## Introduction
	- Allows users to provide their geographical location to web applications
	- Simple and easy to use
	- Only works in secure contexts (https)
- ## navigrator.geolocation
	- First check if the browser supports geolocation
	- ``` js
	  	if (navigator.geolocation) {
	  console.log("Geolocation is supported");
	  	} else {
	  console.error("Geolocation is not supported");
	  	}
	  ```
	- ### getCurrentLocation function
		- This will show a popup asking permission to allow getting the current location
		- Allowing the permission of getting the location will log the GeolocationCoordinates object of type GeolocationPosition
		- Denying will log the GeolocationPositionError
		- ``` js
		  
		  	const successCallback = (position) => {
		  console.log(position);
		  	};
		  	const errorCallback = (error) => {
		  console.error(error);
		  	};
		  	navigator.geolocation.getCurrentLocation(successCallback, errorCallback);
		  ```
		- #### getCurrentLocation options paramter
		- Options parameter gives more paramters for getting the current location
		- ``` js
		  
		  	const successCallback = (position) => {
		  console.log(position);
		  	};
		  	const errorCallback = (error) => {
		  console.error(error);
		  	};
		  	navigator.geolocation.getCurrentLocation(successCallback, errorCallback, {
		  enableHighAccuracy: true,
		  timeout: 5000
		  	});
		  ```
	- ### watchPosition function
		- Function gets the location and continuously updates the user's current location
		- To stop the watch session, use the clearWatch function with the parameter of watchId returned from the watchPosition function
		- ``` js
		  
		  	const successCallback = (position) => {
		  console.log(position);
		  	};
		  	const errorCallback = (error) => {
		  console.error(error);
		  	};
		  	const watchId = navigator.geolocation.watchPosition(successCallback, errorCallback);
		  
		  	navigator.geolocation.clearWatch(watchId);
		  ```