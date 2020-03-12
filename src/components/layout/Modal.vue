<template>
     <div class="">
        <div class="modaloverlay" @click="closeModal"></div>
            <div class="modal">
                <h2>{{ title }}</h2>
                <div class="body">
                    <slot></slot>
                </div>
                <br />
            <button class="close-btn" @click="closeModal">Close</button>
        </div>
    </div>
</template>

<script>
export default {
    name:"Modal",
     props:{
        title:{
            type: String,
            required: true,
        },
    },
    methods:{
        closeModal(){
            this.$emit('closeModal');
        },
    }
}
</script>

<style scoped>
.close-btn{
    padding: 8px;
    background-color: tomato;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 17px;
}
.modal{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 99;
    
    width: 100%;
    max-width: 400px;
    background-color: rgba(0, 0, 0, 0.85);
    border-radius: 16px;
    
    padding: 25px;
    }
 h2 {
    color: #fff;
    font-size: 32px;
    font-weight: 900;
    margin-bottom: 15px;
 }
 
 p {
    color: #fff;
    font-size: 18px;
    font-weight: 400;
    margin-bottom: 15px;
 }

 .modaloverlay {
    position: absolute;
    display: none;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 98;
    background-color: rgba(0, 0, 0, 0.3);
}

</style>