<template lang="html">
  <div class='container'>
    <h1>Map demo</h1>
    <div id="myMap">
      <p>Fetching location and setting up map ... </p>
    </div>
  </div>
</template>

<script>
export default {
    data() {
      return {
          lat: 0.0,
          lng: 0.0,
          map: null
        }
    },

    mounted: function() {
      this.getCurrentLocation()
        .then(()=>{
          this.initMap()
        })
        .catch((err)=>{
          alert(err)
        })
    },

    methods: {
      getCurrentLocation() {
        return new Promise((resolve, reject) =>{
          if ('geolocation' in navigator) {
            var gl = navigator.geolocation
            gl.getCurrentPosition(function(position) {
              this.lng = position.coords.longitude
              this.lat = position.coords.latitude

              let latLng = new google.maps.LatLng(this.lat, this.lng)
            resolve(latLng);

            }.bind(this))
          } else {
            reject('Cannot use geolocation')
          }
        })
      },

      initMap() {
        this.map = new google.maps.Map(document.getElementById('myMap'), {
                   center: {
                     lat: this.lat,
                     lng: this.lng
                   },
                   zoom: 15
               });
      }
  }
}
</script>

<style lang="css">
* {
  margin: 0;
  padding: 0;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  font-size: 15px;
}

html {
  background-size: cover;
  background-position: center;
  max-width: 100vw;
  height: 100vh;
  background-color: #bdc3c7;
}

  h1 {
    color: #e74c3c;
    font-size: 4em;
    font-weight: 400;
    margin-top: 0.5em;
    margin-bottom: 0.5em;
  }

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}

#myMap {
  height: 80vh;
  width: 90vw;
}

#myMap p {
  text-align: center;
  font-size: 2em;
  font-weight: 300;
  line-height: 50vh;
  color: #2c3e50;
}
</style>
