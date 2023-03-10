# `<MapView />` Component API

## Props

| Prop | Type | Default | Note |
|---|---|---|---|
| `provider` | `string` |  | The map framework to use. <br/><br/>Either `"google"` for GoogleMaps, otherwise `null` or `undefined` to use the native map framework (`MapKit` in iOS and `GoogleMaps` in android).
| `region` | `Region` |  | The region to be displayed by the map. <br/><br/>The region is defined by the center coordinates and the span of coordinates to display.
| `initialRegion` | `Region` |  | The initial region to be displayed by the map.  Use this prop instead of `region` only if you don't want to control the viewport of the map besides the initial region.<br/><br/> Changing this prop after the component has mounted will not result in a region change.<br/><br/> This is similar to the `initialValue` prop of a text input.
| `liteMode` | `Boolean` | `false` | Enable lite mode. **Note**: Android only.
| `mapType` | `String` | `"standard"` | The map type to be displayed. <br/><br/> - standard: standard road map (default)<br/> - satellite: satellite view<br/> - hybrid: satellite view with roads and points of interest overlayed<br/> - terrain: (Android only) topographic view
| `showsUserLocation` | `Boolean` | `false` | If `true` the app will ask for the user's location. **NOTE**: You need to add `NSLocationWhenInUseUsageDescription` key in Info.plist to enable geolocation, otherwise it is going to *fail silently*!
| `followsUserLocation` | `Boolean` | `false` | If `true` the map will focus on the user's location. This only works if `showsUserLocation` is true and the user has shared their location. **Note**: iOS only.
| `showsMyLocationButton` | `Boolean` | `true` | `Android only` If `false` hide the button to move map to the current user's location.
| `showsPointsOfInterest` | `Boolean` | `true` | If `false` points of interest won't be displayed on the map.
| `showsCompass` | `Boolean` | `true` | If `false` compass won't be displayed on the map.
| `showsScale` | `Boolean` | `true` | A Boolean indicating whether the map shows scale information.
| `showsBuildings` | `Boolean` | `true` | A Boolean indicating whether the map displays extruded building information.
| `showsTraffic` | `Boolean` | `true` | A Boolean value indicating whether the map displays traffic information.
| `showsIndoors` | `Boolean` | `true` | A Boolean indicating whether indoor maps should be enabled.
| `zoomEnabled` | `Boolean` | `true` | If `false` the user won't be able to pinch/zoom the map.
| `rotateEnabled` | `Boolean` | `true` | If `false` the user won't be able to pinch/rotate the map.
| `scrollEnabled` | `Boolean` | `true` | If `false` the user won't be able to change the map region being displayed.
| `pitchEnabled` | `Boolean` | `true` | If `false` the user won't be able to adjust the camera???s pitch angle.
| `toolbarEnabled` | `Boolean` | `true` | `Android only` If `false` will hide 'Navigate' and 'Open in Maps' buttons on marker press
| `cacheEnabled` | `Boolean` | `false` | If `true` map will be cached and displayed as a image instead of being interactable, for performance usage.
| `loadingEnabled` | `Boolean` | `false` | If `true` a loading indicator will show while the map is loading.
| `loadingIndicatorColor` | `Color` | `#606060` | Sets loading indicator color, default to `#606060`.
| `loadingBackgroundColor` | `Color` | `#FFFFFF` | Sets loading background color, default to `#FFFFFF`.
| `moveOnMarkerPress` | `Boolean` | `true` | `Android only` If `false` the map won't move when a marker is pressed.


## Events

| Event Name | Returns | Notes
|---|---|---|
| `onRegionChange` | `Region` | Callback that is called continuously when the region changes, such as when a user is dragging the map.
| `onRegionChangeComplete` | `Region` | Callback that is called once when the region changes, such as when the user is done moving the map.
| `onPress` | `{ coordinate: LatLng, position: Point }` | Callback that is called when user taps on the map.
| `onPanDrag` | `{ coordinate: LatLng, position: Point }` | Callback that is called when user presses and drags the map. **NOTE**: for iOS `scrollEnabled` should be set to false to trigger the event
| `onLongPress` | `{ coordinate: LatLng, position: Point }` | Callback that is called when user makes a "long press" somewhere on the map.
| `onMarkerPress` |  | Callback that is called when a marker on the map is tapped by the user.
| `onMarkerSelect` |  | Callback that is called when a marker on the map becomes selected. This will be called when the callout for that marker is about to be shown. **Note**: iOS only.
| `onMarkerDeselect` |  | Callback that is called when a marker on the map becomes deselected. This will be called when the callout for that marker is about to be hidden. **Note**: iOS only.
| `onCalloutPress` |  | Callback that is called when a callout is tapped by the user.
| `onMarkerDragStart` | `{ coordinate: LatLng, position: Point }` | Callback that is called when the user initiates a drag on a marker (if it is draggable)
| `onMarkerDrag` | `{ coordinate: LatLng, position: Point }` | Callback called continuously as a marker is dragged
| `onMarkerDragEnd` | `{ coordinate: LatLng, position: Point }` | Callback that is called when a drag on a marker finishes. This is usually the point you will want to setState on the marker's coordinate again



## Methods

| Method Name | Arguments | Notes
|---|---|---|
| `animateToRegion` | `region: Region`, `duration: Number` |
| `animateToCoordinate` | `region: Coordinate`, `duration: Number` |
| `fitToElements` | `animated: Boolean` |
| `fitToSuppliedMarkers` | `markerIDs: String[]` | If you need to use this in `ComponentDidMount`, make sure you put it in a timeout or it will cause performance problems.
| `fitToCoordinates` | `coordinates: Array<LatLng>, edgePadding: EdgePadding, animated: Boolean` |



## Types

```
type Region {
  latitude: Number,
  longitude: Number,
  latitudeDelta: Number,
  longitudeDelta: Number,
}
```

```
type LatLng {
  latitude: Number,
  longitude: Number,
}
```

```
type Point {
  x: Number,
  y: Number,
}
```

```
enum MapType : String {
  "standard",
  "satellite",
  "hybrid",
  "terrain" //Android only
}
```

```
type EdgePadding {
  top: Number,
  right: Number,
  bottom: Number,
  left: Number
}
```
