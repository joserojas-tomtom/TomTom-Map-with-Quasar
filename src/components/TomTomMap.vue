<template>
  <div id='map' class='window-height'>
    <TomTomSearch :city='city'
    @cityFound='handleSearchResult'
    :apikey='apikey'/>
  </div>
</template>

<script>
import tt from '@tomtom-international/web-sdk-maps'
import TomTomSearch from 'components/Search.vue'
export default {
  name: 'TomTomMap',
  props: ['city', 'apikey'],
  components: { TomTomSearch },
  methods: {
    handleSearchResult (location) {
      this.ttmap.easeTo({
        center: location,
        zoom: 16
      })
    }
  },
  mounted () {
    this.ttmap = tt.map({
      container: 'map',
      key: this.apikey
    })
  },
  data () {
    return {
      ttmap: undefined
    }
  }
}
</script>
