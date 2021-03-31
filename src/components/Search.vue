<template>
  <div class='text-h4'>{{ cityName }}</div>
</template>

<script>
import tt from '@tomtom-international/web-sdk-services'

export default {
  name: 'TomTomSearch',
  props: ['apikey', 'city'],
  mounted () {
    const _this = this
    tt.services.fuzzySearch({
      key: this.apikey,
      query: this.city
    }).then(function (response) {
      console.log(response)
      _this.$emit('cityFound', response.results[0].position)
      _this.cityName = response.results[0].address.freeformAddress + ' ' +
      response.results[0].address.country
    })
  },
  data () {
    return {
      cityName: 'Hello, I am searching...'
    }
  }
}
</script>
