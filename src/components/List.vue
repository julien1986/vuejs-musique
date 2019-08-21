<template>
  <div>
    <ul>
      <morceau
        v-for="(item, index) in playlist"
        :morceau="item"
        :KeyID="index"
        @validation="validation"
        @supprimer="supprimer"
      ></morceau>
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
  },
  methods:{
    validation(id){
      console.log(id)
      this.$emit("validation2", id);
    },
    supprimer(id){
      this.$emit("supprimer2", id)
    }
  }
}
</script>

<style lang="scss">
</style>
