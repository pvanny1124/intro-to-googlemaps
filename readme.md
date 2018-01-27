Introduction to the google maps API!

Here I show:

1) how to initialize a map and dump it into html,
2) how to add a marker with different properties such as a custom image icon, latitude and longitude, 
    and a pop-up window with text.
3) how to add a marker anywhere on the map when a user clicks on any region in the map

Overview:

1) Get a google API key for free on google developers,
2) Copy/paste script:

     <script src="https://maps.googleapis.com/maps/api/js?key=<KEY GOES HERE>&callback=initMap"
            async defer></script>
            
            -callback is looking for the function: initMap()
            
3) create initMap() function:

        //create Map options to be passed into our map
        
                    var options = {
                        zoom: 10,
                        center: {lat: 40.7128, lng: -74.0060}
                    }

         var map = new google.maps.Map(document.getElementById("map"), options);
            //create a map object
    
       
4) setup a div with the id of "map" wherever you want to place the map in your html:

         <div id="map"></div>
                   
5) style the map id with the height/width proportions to actually see the map:

          <style>
            #map {
                height: 400px;
                width: 100%;
            }
          </style>

To create multiple markers:
1) create array with objects with custom properties that you will include in each marker --notes in code
2) loop through the array and create a new marker with each object in the array

To create a single marker:

         var marker = new google.maps.Marker(options);
         
To create an infoWindow:

        var infoWindow = new google.maps.InfoWindow({
                        content: <text>
                    });
                    
To add click listener for a marker:

        marker.addListener("click", function(){
            infoWindow.open(map, marker);
            //where map is the map that we created in the code, and marker is the variable marker that we created. (see code)
        });
        
To add a marker anywhere on the map with a click:

         //add listen for click on map to add a marker where that click happened
         
                    google.maps.event.addListener(map, "click", function(event){
                        addMarker({coords: event.latLng});
                        //event.latLng gets the coordinates of wherever you click in the map
                    });