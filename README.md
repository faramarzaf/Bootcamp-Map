# Bootcamp-Map  


**Step 1.** Open Google developer console and signin with your gmail account: https://console.developers.google.com/project  


**Step 2.** Now create new project. You can create new project by clicking on the Create Project button and give name to your project.  
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Create-new-project.png" /> 
</p>


**Step 3.** Now click on APIs & Services and open Dashboard from it.   
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Open-Dashboard.png" /> 
</p>

**Step 4.** Open Enable APIS AND SERICES.  
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Enable-api.png" /> 
</p>


**Step 5.** Now open Google Map Android API.  
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/open-google-map-api.png" /> 
</p>



**Step 6.** Now enable the Google Maps Android API.  
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Enable-Google-Maps-API.png" /> 
</p>


**Step 7.** Now go to Credentials.  
<p align="center">
  <img src="https://abhiandroid.com/programming/wp-content/uploads/2018/01/Open-Credentials.png" /> 
</p>


**Step 8.** Here click on Create credentials and choose API key.
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Create-Google-Map-API-credentials.png" /> 
</p>

**Step 9.** Now API your API key will be generated. Copy it and save it somewhere as we will need it when implementing Google Map in our Android project.  
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Google-Map-api-key-created.png" /> 
</p>

**Now paste API key here:**
<p align="center">
  <img src="https://abhiandroid-8fb4.kxcdn.com/programming/wp-content/uploads/2018/01/Google-Maps-API-xml-android-studio.png" /> 
</p>


**Display a map, using the Maps SDK for Android**  

Add a `<fragment>` element to your activity's layout file, `activity_maps.xml`. This element defines a *SupportMapFragment* to act as a container for the map and to provide access to the GoogleMap object.
   ```xml
    <fragment xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:id="@+id/map"
        android:name="com.google.android.gms.maps.SupportMapFragment"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context="com.example.mapwithmarker.MapsMarkerActivity" />
```
In your activity's `onCreate()` method, set the layout file as the content view.  

Get a handle to the map fragment by calling `FragmentManager.findFragmentById()`. Then use `getMapAsync()` to register for the map callback.  
```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    // Retrieve the content view that renders the map.
    setContentView(R.layout.activity_maps);
    // Get the SupportMapFragment and request notification
    // when the map is ready to be used.
    SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
            .findFragmentById(R.id.map);
    mapFragment.getMapAsync(this);
}
```
Implement the `OnMapReadyCallback` interface and override the `onMapReady()` method, to set up the map when the GoogleMap object is available.  
```java
public class MapsMarkerActivity extends AppCompatActivity
        implements OnMapReadyCallback {
    // Include the OnCreate() method here too, as described above.
    @Override
    public void onMapReady(GoogleMap googleMap) {
        // Add a marker in Sydney, Australia,
        // and move the map's camera to the same location.
        LatLng sydney = new LatLng(-33.852, 151.211);
        googleMap.addMarker(new MarkerOptions().position(sydney)
                .title("Marker in Sydney"));
        googleMap.moveCamera(CameraUpdateFactory.newLatLng(sydney));
    }
}
```









