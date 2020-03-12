<template>
    <div class="Noteitem">
        <Modal 
        title="Edit this Note"
        v-if="notes.edit"
        @closeModal="showModal" 
         >
            <hr>
            <label for="noteTitle"> Title:
                <input type="text" class="inputs" name="noteTitle" v-model="notes.title" placeholder="title">
            </label>
            <br />
            <label for="notebody" > Note:
                <textarea class="inputs" name="notebody" v-model="notes.body" cols="30" rows="10"></textarea>
            </label>
        </Modal>

        <div class="card">
            <button @click="showModal" class="edit-btn">Edit</button>
            <button @click="$emit('deleteNotes', notes.id)" class="delete-btn">Delete</button>
            <h3>{{ notes.title }}</h3>
            <hr>
            <p>{{ notes.body }}</p>
        </div>

    </div>
</template>

<script>

import Modal from './layout/Modal.vue';

export default {
    name:"NoteItem",
    components:{
        Modal,
    },
    props:{
        notes: Object
    },
    data(){
        return {
            modalShown:false,
            noteTitle: "",
            noteBody: "",
        }
    },
    methods:{
        showModal()
        {
            this.notes.edit = !this.notes.edit;
        },
    }
}
</script>

<style scoped>

.card {
    margin: 30px auto;
    width: 300px;
    height: 300px;
    border-radius: 40px;
    box-shadow: 0px 0px 20px 3px rgba(0,0,0,0.15);
    cursor: pointer;
    transition: 0.4s;
    background: ghostwhite;
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
.edit-btn{
    background:teal;
    color:white;
    border: none;
    border-radius: 0px 0px 0px 15px;
    padding: 5px;
    width: 60px;
}
.delete-btn{
    background: tomato;
    color:white;
    border: none;
    border-radius: 0px 0px 15px 0px;
    padding: 5px;
    width: 60px;
}

</style>