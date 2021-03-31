<template>
  <q-page class="flex-center">
    <TomTomMap city='Portland, OR' apikey='GET YOUR OWN API KEY! :) '/>
  </q-page>
</template>

<script>
import TomTomMap from 'components/TomTomMap.vue'
export default {
  name: 'PageIndex',
  components: { TomTomMap }
}
</script>
