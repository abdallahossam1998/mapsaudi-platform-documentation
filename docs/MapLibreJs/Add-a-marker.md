# Add a marker

Estimated reading time : 1 minutes

Check out this code sample that uses the MapLibre GL JS library to add a marker from GeoJSON onto your map.

```
<!DOCTYPE html>
<html>
<head>
  <meta charset=UTF-8>
  <link href="https://unpkg.com/maplibre-gl@2.1.9/dist/maplibre-gl.css" rel="stylesheet" />
  <script src="https://unpkg.com/maplibre-gl@2.1.9/dist/maplibre-gl.js"></script>
  <style>
    body {
      margin: 0;
      padding: 0;
    }
    #map {
      min-height: 500px;
      height: 100%;
      width: 100%;
    }
    .marker {
      background-image: url('https://www.jawg.io/docs/images/icons/eiffel-tower@2x.png');
      background-size: cover;
      width: 50px;
      height: 50px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="map"></div>
  <script>
    // Don't forget to replace <YOUR_ACCESS_TOKEN> by your real access token! 
    const accessToken = '<YOUR_ACCESS_TOKEN>';
    const map = new maplibregl.Map({
      container: 'map',
      style: `https://api.jawg.io/styles/jawg-terrain.json?access-token=${accessToken}`,
      zoom: 11,
      center: [2.349902, 48.852966],
    }).addControl(new maplibregl.NavigationControl(), 'top-right');
    // This plugin is used for right to left languages
    maplibregl.setRTLTextPlugin('https://unpkg.com/@mapbox/mapbox-gl-rtl-text@0.2.3/mapbox-gl-rtl-text.min.js');

    // This add a marker with the default icon
    new maplibregl.Marker().setLngLat([2.349902, 48.852966]).addTo(map);
    // Marker with custom icon
    const el = document.createElement('div');
    el.className = 'marker';
    new maplibregl.Marker(el)
      .setLngLat([2.294694, 48.858093])
      .addTo(map);
  </script>
</body>
</html>
```