<template>
  <div>
    <h1>La liste des musiques:</h1>
    <hr>
    <div>
      <list :playlist="playlist" @validation2="update_data" @supprimer2="delete_item"></list>
    </div>
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
      sync()
    },
    update_data(id){
      console.log(id)
      this.playlist[id].data_chekbox = true 
      sync()
    },
    delete_item(id){
      this.playlist.splice(id, 1)
      sync()
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