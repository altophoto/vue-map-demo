<template>
  <div id="app">
    <app-map></appp-map>
  </div>
</template>

<script>
import Map from './components/Map.vue'
export default {
  name: 'app',
  components: {
    'app-map': Map
  }
}
</script>
