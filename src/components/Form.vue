<template>
  <section class="form">
    <h3>Proposer un morceau de musique :</h3>
    <b-field label="nom du groupe">
      <b-input v-model="send_list.group_name"></b-input>
    </b-field>
    <b-field label="nom du morceau">
      <b-input v-model="send_list.musique_name"></b-input>
    </b-field>
    <b-button @click.prevent="data_send" type="is-success">Envoyer</b-button>
  </section>
</template>

<script>
export default {
  name: 'Form',
  data(){
      return{
        send_list:{
            group_name:"",
            musique_name:"",
            data_chekbox: false
          }
      }
    },
    methods:{
      data_send(){
        let value = this.send_list
        this.$emit("data_send", value)
        this.send_list= {
            group_name:"",
            musique_name:"",
            data_chekbox: false
          }
      }
    }
}
</script>

<style lang="scss">
</style>


