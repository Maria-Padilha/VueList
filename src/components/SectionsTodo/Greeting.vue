<template>
    <section class="greeting">
        <h2 class="title">
            Como vai, <input type="text" placeholder="Seu nome" v-model="name">
        </h2>
        
    </section>
</template>

<script>
    import { ref } from 'vue';

    export default{
        data(){
            return{
                name: ref('')
            }
        },
        watch: {
            name(newName, name){
            localStorage.setItem('name', newName)
        },
        },
        mounted(){
            this.name = localStorage.getItem('name') || ''
        }
    }
</script>