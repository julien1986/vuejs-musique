<template>
  <li :class="{'data_chekbox':morceau.data_chekbox}">
    <div>
      <strong>{{ morceau.group_name }}</strong>
      :&nbsp{{morceau.musique_name}}&nbsp
    </div>
    <a href="#">
      <div class="check"></div>
    </a>
  </li>
</template>

<script>
export default {
  name: "morceau",
  props:["morceau"]
}
</script>

<style lang="scss">
li {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  color: red;

  .true {
    color: green;
  }
  .check {
    width: 15px;
    height: 15px;
    border: 2px solid black;
    margin-top: 5px;
    margin-left: 5px;
  }
}
</style>
