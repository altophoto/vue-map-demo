<template lang="html">
  <div>
    <h1>Map</h1>

    <div id="myMap"></div>
  </div>
</template>

<script>
export default {
    data() {
      return {

      }
    },
    mounted: function() {
      this.initMap();
    },
  methods: {
    initMap() {
      console.log('initMap');
      map = new google.maps.Map(document.getElementById('myMap'), {
                 center: {lat: 51.507351, lng: -0.127758},
                 zoom: 12
             });
    }
  }
}
</script>

<style lang="css">
#myMap {
  height: 400px;
  width: 400px;
  border: 1px solid black;
}
</style>
