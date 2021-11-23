<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="map"></div>
  </div>
</template>
<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}
</style>
<script>
/* global mapboxgl */
export default {
  mounted: function () {
    this.setUpMap();
  },
  methods: {
    setUpMap: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MAP_API_KEY;
      const map = new mapboxgl.Map({
        container: "map", // container ID
        style: "mapbox://styles/mapbox/streets-v11", // style URL
        center: [12.554729, 55.70651], // starting position [lng, lat]
        zoom: 9, // starting zoom
      });
      // create the popup
      const popup = new mapboxgl.Popup({ offset: 25 }).setText(
        "Construction on the Washington Monument began in 1848."
      );
      // Create a default Marker and add it to the map.
      const marker1 = new mapboxgl.Marker().setLngLat([12.554729, 55.70651]).setPopup(popup).addTo(map);
      console.log(map, marker1, popup);
      // create the marker
    },
  },
};
</script>
