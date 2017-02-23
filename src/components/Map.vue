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
          lat: 51.507351,
          lng: -0.127758,
          map: null
        }
    },
    created(){
      this.getCurrenttLocation();
    },

    mounted: function() {
      this.initMap();
    },

    methods: {
      getCurrenttLocation() {
        if ('geolocation' in navigator) {
          var gl = navigator.geolocation
          gl.getCurrentPosition(function(position) {
            console.log(position.coords);
            this.lng = position.coords.longitude
            this.lat = position.coords.latitude

            let latLng = new google.maps.LatLng(this.lat, this.lng)
            // this.map.setCenter(latLng);

            this.map.panTo(latLng);

          }.bind(this))
        }
      },

      initMap() {
        console.log('initMap');
        this.map = new google.maps.Map(document.getElementById('myMap'), {
                   center: {
                     lat: this.lat,
                     lng: this.lng
                   },
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
