<template>
  <li>
    <div :class="{'data_chekbox':morceau.data_chekbox}">
      <strong>{{ morceau.group_name }}</strong>
      :&nbsp{{morceau.musique_name}}&nbsp
    </div>
    <button v-if="morceau.data_chekbox == true" @click="validation" class="check">Valider</button>
    <button v-else @click="supprimer" class="check">Supprimer</button>
  </li>
</template>

<script>
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
