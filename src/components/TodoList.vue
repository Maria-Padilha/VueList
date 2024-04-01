<template>
    <main class="app">
        <Greeting />
        <CreateTodo />
    </main>
</template>

<script>
    import Greeting from '@/components/SectionsTodo/Greeting.vue'
    import CreateTodo from '@/components/SectionsTodo/CreateTodo.vue'
    export default{
        components:{
            Greeting,
            CreateTodo
        }
    }
</script>