<template>
  
  <div id="app">

    <Header />
    <div class="add-notes-bar">
    <Add-note @newnote="addNote" @notes="notes"/>
    <h3 id="notes-counter">Notes: <span id="Counter">{{ notes.length }} </span></h3>
    </div>
    
      <Notes v-bind:mynotes="notes" @deleteNotes="deleteNote" />
      
  </div>
</template>

<script>

import Header from './components/layout/Header.vue';
import AddNote from './components/AddNote.vue';
import Notes from './components/Notes.vue';

export default {
  name: 'App',
  components: {
    Header,
    AddNote,
    Notes,
  },
  data(){
    return{
      notes:[
        {
          id:1,
          title:'Yesterday was great day',
          body:'i had good day yesterday',
          edit: false,
        },
        {
          id:2,
          title:'i went to paris in 2005',
          body:'paris is beautiful',
          edit: false,
        },
        {
          id:3,
          title:'my favorite movie is inception',
          body:'inception is best movie i have ever seen',
          edit: false,
        }

      ],
    }
  },
  methods:{
    addNote(newnote){
      this.notes.push(newnote);
    },
    deleteNote(id){
      this.notes = this.notes.filter(note => note.id !== id );
    }
  }
}
</script>

<style>
body{
  background: whitesmoke;
}
.add-notes-bar{
  display: inline-block;
  background: white;
  width: 50%;
  box-shadow: 0px 0px 20px 3px rgba(0,0,0,0.15);
  border-radius: 0px 0px 20px 20px;
}
#notes-counter{
  float: left;
  margin-left: 15px;
}
#Counter{
  color: #1a7186;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
