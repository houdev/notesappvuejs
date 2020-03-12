<template>
    <div class="addnote">
        <transition name="fade">
            <Modal 
                title="Add New Note" 
                v-if="modalShown" 
                @closeModal="toggleModal" >

                <hr>

                <label for="noteTitle"> Title:
                    <input type="text" class="inputs" name="noteTitle" v-model="noteTitle" placeholder="title">
                </label>

                <br />

                <label for="notebody" > Note:
                    <textarea class="inputs" name="notebody" v-model="noteBody" cols="30" rows="10"></textarea>
                </label>

                <br />

                <button 
                    @click="addNotes" 
                    :disabled="noteTitle.length < 3" 
                    class="add-btn" 
                    id="add-this-note"
                >
                    Add this Note
                </button>

            </Modal>
        </transition>
        <button 
          @click="toggleModal" 
          class="add-btn" 
          id="add-note-home"
        >
          Add Note
        </button>

    </div>
</template>

<script>

import Modal from './layout/Modal.vue';


export default {
    name:"AddNote",
    components: {
    Modal
  },
   props:{
       mynotes: Object,
   },
    data(){
        return {
           modalShown: false,
           noteTitle: "",
           noteBody: "",
           notes2: this.mynotes,
           notesCount: "",

        }
    },
    methods:{
      toggleModal(){
        this.modalShown = !this.modalShown;
            },
      addNotes(){
        const newNote = {
              id: Math.round(Math.random() * 1000),
              title: this.noteTitle,
              body: this.noteBody,
              edit: false,
            }
        this.$emit('newnote', newNote);
        this.noteTitle = "";
        this.noteBody = "";

        },
    },
    
}
</script>

<style scoped>
h4{
    display: inline;

}
#add-this-note{
    width: 50%;
    font-size: 17px;
}
#add-note-home{
    float: right;
    margin-top: 14px;
    margin-right: 15px;
}
.add-btn{
    padding: 8px;
    background-color: rgb(51, 139, 88);
    color: white;
    border: none;
    border-radius: 5px;

}
.add-btn:disabled{
    padding: 8px;
    background-color: rgb(124, 124, 124);
    color: white;
    border: none;
    border-radius: 5px;
}
.inputs{
    background-color: black;
    color: #fff;
    border-radius: 8px;
    padding: 8px;
    display: inline;
    font-size: 17px;
}
label{
    color:white;
    display: grid;
}
</style>