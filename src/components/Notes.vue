<template>
    <div class="notes" >
        <div class="cards-list">
            <div v-bind:key="notes.id"  v-for="notes in mynotes">

                <Note-item v-bind:notes="notes" @deleteNotes="$emit('deleteNotes', notes.id)" />

            </div>
        </div>
    </div>
</template>

<script>

import NoteItem from './NoteItem.vue';

export default {
    name:"Notes",
    components:{
        NoteItem,
    },
    props:{
        mynotes: Array,
    }
}
</script>

<style scoped>
.cards-list {
    z-index: 0;
    width: 100%;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
#mynotes{
    display: inline;
}
</style>