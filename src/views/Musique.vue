<template>
  <div>
    <h1>La liste des musiques:</h1>
    <hr>
    <list :playlist="playlist" @validation2="update_data" @supprimer2="delete_item"></list>
    <hr>
    <Form @data_send="update_list"></Form>
  </div>
</template>


<script>
// @ is an alias to /src
import list from '@/components/List.vue'
import Form from '@/components/Form.vue'

export default {
  name: 'Musique',
  components: {
    list,
    Form
  },
  data() {
    return { 
      playlist:[
      {
        group_name:"Metallica",
        musique_name:"un truc",
        data_chekbox:true
      },
      {
        group_name:"Metallica",
        musique_name:"un truc",
        data_chekbox:false
      }
    ]
  } },
  props: ["liste"],
  methods:{
    update_list(the_song){
      this.playlist.push(the_song)
      this.$buefy.snackbar.open({
        message: 'Morceau ajouté',
        type: 'is-warning',
        position: 'is-top',
        actionText: 'Annuler',
          onAction: () => {
            this.playlist.pop()
            this.$buefy.toast.open({
              message: 'Action annulée',
              queue: false
            })
            this.sync()
          }
      })
      this.sync()
    },
    update_data(id){
      this.playlist[id].data_chekbox = true 
      this.sync()
      this.$buefy.snackbar.open({
        message: 'Morceau validé',
        type: 'is-warning',
        position: 'is-top',
        actionText: 'Annuler',
          onAction: () => {
            this.playlist[id].data_chekbox = false
            this.$buefy.toast.open({
              message: 'Action annulée',
              queue: false
            })
            this.sync()
          }
      })
    },
    delete_item(id){
      this.playlist.splice(id, 1)
      this.sync()
    },
    sync(){
      localStorage.setItem("playlist", JSON.stringify(this.playlist))
      
    }
  },
  created(){
    if(localStorage.playlist){
      this.playlist = JSON.parse(localStorage.getItem("playlist"))
    }
  }
}
</script>