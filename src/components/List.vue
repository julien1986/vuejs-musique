<template>
  <div>
    <ul>
      <morceau v-for="item in playlist" :morceau="item"></morceau>
    </ul>
  </div>
</template>


<script>
import morceau from '@/components/Morceau.vue'

export default {
  name: 'list',
  props:{
    playlist: Array
  },
  components: {
    morceau
  }
}
</script>

<style lang="scss">
</style>
