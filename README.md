


# Welcome to Map Codelab
### Hi there , this codelab will show you have to implement Google map on you android project.
![enter image description here](https://raw.githubusercontent.com/FirasShawa/GoogleMapStartUp/main/images/googlemap.png)




# Dependency
we are going to use google map dependency:

    implementation 'com.google.android.gms:play-services-maps:17.0.0'

# CodeLab Start  🤖


Donwload the start up project zip file : [Start Up Project](https://github.com/FirasShawa/GoogleMapStartUp/archive/main.zip)
 - [Google Map locaiton](https://www.google.com/maps/place/45%C2%B026%2716.5%22N+12%C2%B019%2733.7%22E/@45.4379137,12.3238383,17z/data=!3m1!4b1!4m14!1m7!3m6!1s0x0:0x0!2zNDXCsDI2JzE3LjIiTiAxMsKwMTknMDUuNiJF!3b1!8m2!3d45.438122!4d12.318221!3m5!1s0x0:0x0!7e2!8m2!3d45.4379102!4d12.3260265)

Let's start 🤖
## 1-MapView

Activity Name : MapViewActivity.kt
Layout Name: activity_map_view_activity.xml
Goal : Show Map on your emulator.

### XML
**TODO: 1.1**
Go to res -> layput -> activity_map_view_activity.xml and add the following code.

    <!--//TODO: 1.1 Add MapView to this activity XML-->
    <com.google.android.gms.maps.MapView  
      android:id="@+id/mapViewXML"  
      android:layout_width="match_parent"  
      android:layout_height="match_parent"  />

### Code

**TODO: 1.2** -> Implement OnMapReady on the class definition:

    //TODO: 1.2 Implement OnMapReady on the class definition
    class MapViewActivity : AppCompatActivity() ,OnMapReadyCallback{}

    
 **TODO: 1.3** -> Add the variables and the companion object :

    //TODO: 1.3 Add the variables and the companion object
     companion object{  
        private const val MAPVIEW_BUNDLE_KEY = "MapViewBundleKKey"
        }
        private lateinit var mapView: MapView
.
 **TODO: 1.4** -> Complete OnCreate function.

    //TODO 1.4 Complete OnCreate function
     override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_map_view)  
    
      val mapViewBundle = savedInstanceState?.getBundle(MAPVIEW_BUNDLE_KEY)  
    
      mapView = mapViewXML  
        mapView.onCreate(mapViewBundle)  
        mapView.getMapAsync(this)  
    }

 **TODO: 1.5** -> Complete onSaveInstanceState function.

    //TODO: 1.5 Complete onSaveInstanceState function
     override fun onSaveInstanceState(outState: Bundle) {  
        super.onSaveInstanceState(outState)  
        val mapViewBundle = outState.getBundle(MAPVIEW_BUNDLE_KEY)?: Bundle().apply {  
      putBundle(MAPVIEW_BUNDLE_KEY,this)  
        }  
      mapView.onSaveInstanceState(mapViewBundle)  
    }

 **TODO: 1.6** -> Complete Override onMapReady function.

    //TODO: 1.6 Complete Override onMapReady function
     override fun onMapReady(map: GoogleMap?) {  
      
    }

 **TODO: 1.7** -> Complete the life cycle functions.

    //TODO: 1.7 Complete the life cycle functions
    override fun onStart() {  
        super.onStart()  
        mapView.onResume()  
    }  
      
    override fun onResume() {  
        super.onResume()  
        mapView.onResume()  
    }  
      
    override fun onStop() {  
        super.onStop()  
        mapView.onStop()  
    }  
      
    override fun onPause() {  
        super.onPause()  
        mapView.onStop()  
    }  
      
    override fun onDestroy() {  
        super.onDestroy()  
        mapView.onDestroy()  
    }
Finally **Run your project!**.
## 2-Support MapFragment

Activity Name : SupportMapFragmentActivity.kt
Layout Name: activity_support_map_fragment.xml
Goal : Show Map on your emulator.

### XML
**TODO: 2.1**
Go to res -> layput -> activity_support_map_fragment.xml and add the following code.

<!--//TODO: 2.1 Add fragment  to this activity XML-->
    <fragment  
      android:layout_width="match_parent"  
      android:layout_height="match_parent"  
      android:name="com.google.android.gms.maps.SupportMapFragment"  
      android:id="@+id/MapFragmentXML"  
      />

### Code

**TODO: 2.2** -> Implement OnMapReady on the class definition:

    //TODO: 2.2 Implement OnMapReady on the class definition
    class SupportMapFragmentActivity : AppCompatActivity() , OnMapReadyCallback {}

**TODO: 2.3 Complete OnCreate**

    //TODO: 2.3 Complete OnCreate
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_map_fragment)  
      
        val mapFragment = supportFragmentManager  
      .findFragmentById(R.id.MapFragmentXML) as SupportMapFragment  
      
        mapFragment.getMapAsync(this)  
      
    }

**TODO: 2.4** -> Complete Override onMapReady function

    //TODO: 2.4 Complete Override onMapReady function.
        override fun onMapReady(map : GoogleMap?) {  

        }
    

## 3-Marker
Activity Name : Markers.kt
Layout Name: activity_markers.xml
Goal : Place a marker on the Map.
### Code

**TODO: 3.1** -> Setup a position  :

    //TODO: 3.1 Setup a position
    var position = LatLng(lat,lng)  //24.788571, 46.805764

**TODO: 3.2** -> Create variable to hold the marker  :

    //TODO: 3.2 Create variable to hold the marker ID
    val marker = MarkerOptions().position(position)  
    
**TODO: 3.3** -> Add the marker to the map  :

    //TODO: 3.3 Add the marker to the map
    map!!.addMarker(marker)

**Short Way**
    
    map!!.addMarker
	    MarkerOptions()
		    .position(LatLng(24.788571, 46.805764)
		    )
	    )

## 4-Polyline
Activity Name : Polylines.kt
Layout Name: activity_polyline.xml
Goal : Draw a polyline on the Map.### Code

**TODO: 4.1** -> specify your points  :

    //TODO: 4.1 -> specify your point
    var point1 = LatLng(24.788571,46.805764)  //24.788571, 46.805764  
    var point2 = LatLng(24.788571,46.805764)  //24.788571, 46.805764  

**TODO: 4.2** ->  Add your points to a Mutable List of LatLng   :

    //TODO: 4.2 -> Add your points to a Mutable List of LatLng
    var points = mutableListOf<LatLng>()  
    points.add(point1)  
    points.add(point2)     

 
**TODO: 4.3** -> Create Polyline and specify the color  :

    //TODO: 4.3 -> Create Polyline and specify the color
    var polyline = PolylineOptions().addAll(points).color(Color.BLUE)  

**TODO: 4.4** -> Add the Polyline to the map  :

    //TODO: 4.4 -> Add the Polyline to the map
    map!!.addPolyline(polyline)

  
**Short Way**
    
    map!!.addPolyline(
		    PolylineOptions()
			    .add(LatLng(1.2,2.3),LatLng(2.0,30.0))
			    .width(2f)
		    .	color(Color.BLUE)
	    )

## 5-Polygon
Activity Name : Polygons.kt
Layout Name: activity_polygon.xml
Goal : Draw a polygon on the Map.
### Code

**TODO: 5.1** -> specify your 3 or more points    :

    //TODO: 5.1 -> specify your 3 or more points
    var point1 = LatLng(24.788571,46.805764)  //24.788571, 46.805764  
    var point2 = LatLng(24.788571,46.805764)  //24.788571, 46.805764  
    var point3 = LatLng(24.788571,46.805764)  //24.788571, 46.805764    

**TODO: 5.2** ->  Add your points to a Mutable List of LatLng   :

    //TODO: 5.2 -> Add your points to a Mutable List of LatLng
    var points = mutableListOf<LatLng>()  
    points.add(point1)  
    points.add(point2)  
    points.add(point3)     

 
**TODO: 5.3** -> Create Polygon and specify the fill color and stroke color   :

    //TODO: 5.3 -> Create Polygon and specify the fill color and stroke color
    var polygon = PolygonOptions()  
				        .addAll(points)  
				        .fillColor(Color.GRAY)  
				        .strokeColor(Color.BLUE)  

  **TODO: 5.4** -> Add the Polygon to the map  :

    //TODO: 5.4 -> Add the Polygon to the map
    map!!.addPolygon(polygon)

**Short Way**
    
    map!!.addPolygon(
			 PolygonOptions()
 				 .add(LatLng(1.0,2.0),LatLng(1.0,2.0),LatLng(1.0,2.0))
    			 .fillColor(Color.GRAY)
    			 .strokeColor(Color.BLUE)
    	 )



## 6-Circle
Activity Name : Circles.kt
Layout Name: activity_circles.xml
Goal : Draw a polygon on the Map.
### Code

**TODO: 6.1** -> specify the center    :

    //TODO: 6.1 -> specify the center
    var center = LatLng(1.1,2.2)  

 
**TODO: 6.2** -> specify the radius   :

    //TODO: 6.2 -> specify the radius
    var radius = 50.0  

 
**TODO: 6.3** -> Create Circle and specify the fill color and stroke colo   :

    //TODO: 6.3 -> Create Circle and specify the fill color and stroke color
    var circle = CircleOptions().center(center).radius(radius).fillColor(Color.BLUE)  

**TODO: 6.4** -> Add the Polygon to the map     :
    
    //TODO: 6.4 -> Add the Polygon to the map
    map!!.addCircle(circle)
**Short Way**

     map!!.addCircle(
		     CircleOptions()
			     .center(LatLng(1.1,2.2))
			     .radius(50.0)
			     .fillColor(Color.BLUE)
	     )



# congratulations 🎊
#### Thank you for completeing the this codelab🥳.
#### if you have any questions please let me know 🧙
