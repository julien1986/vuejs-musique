<template>
  <li>
    <div :class="{'data_chekbox':morceau.data_chekbox}">
      <strong>{{ morceau.group_name | inconnu | cap}}</strong>
      :&nbsp{{morceau.musique_name | cap}}&nbsp
    </div>
    <button v-if="morceau.data_chekbox == true" @click="supprimer" class="check">Supprimer</button>
    <button v-else @click="validation" class="check">Valider</button>
  </li>
</template>

<script>
import capitalize from '@/filters/capitalize'
import inconnu from '@/filters/inconnu'

export default {
  name: "morceau",
  props:["morceau", "KeyID"],
  methods:{
    validation(){
      this.$emit("validation", this.KeyID)
    },
    supprimer(){
      this.$emit("supprimer", this.KeyID)
    }
  },
  filters:{
    cap: capitalize,
    inconnu: inconnu
  }
}
</script>

<style lang="scss">
li {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  color: red;

  .check {
    margin-top: 5px;
    margin-left: 5px;
  }
}
.data_chekbox {
  color: green;
  > * {
    color: green;
  }
}
</style>
