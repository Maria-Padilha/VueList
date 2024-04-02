<template>
    <section class="create-todo">
        <h3>Lista de tarefas</h3>
        <form @submit.prevent="addTodo">
            <h4>Vamos adicionar suas tarefas</h4>
            <h4 class="error" v-if="error">Erro: Campos sem preencher!</h4>
            <input type="text" placeholder="estudar vue" v-model="input_content">
            <h4>Escolha uma categoria</h4>
            <div class="options">
                <label>
                    <input type="radio" name="category" id="category1" value="business" v-model="input_category">
                    <span class="bubble business"></span>
                    <div>Serviço</div>
                </label>
                <label>
                    <input type="radio" name="category" id="category2" value="personal" v-model="input_category">
                    <span class="bubble personal"></span>
                    <div>Pessoal</div>
                </label>
            </div>
            <input type="submit" value="Add Tarefa">
        </form>
    </section>

    <section class="todo-list">
          <h3>Seus Compromissos</h3>
          <div class="list">
              <div v-for="todo in todos_asc" :class="`todo-item ${todo.done && 'done'}`">
                  <label>
                      <input type="checkbox" v-model="todo.done">
                      <span :class="`bubble ${todo.category}`"></span>
                  </label>

                  <div class="todo-content">
                      <input type="text" v-model="todo.content">
                  </div>

                  <div class="actions">
                      <button class="delete" @click="removeTodo">Apagar</button>
                  </div>
              </div>
          </div>
      </section>
</template>

<script>
    export default{
        data(){
            return{
               todos: [],
               input_content: '',
               input_category: null,
               error: false
            }
        },
        methods: {
            addTodo(){
                if(this.input_content === '' || this.input_category === null){
                    this.error = true
                }else{
                    this.error = false
                    this.todos.push({
                        content: this.input_content, 
                        category: this.input_category,
                        done: false,
                        createdAt: new Date().getTime()
                    })
                    this.input_content = ''
                }
            },
            todos_asc(){
                console.log('chegou aqui')
            }
        }, 
        watch: {
            todos:{
                handler(newTodo, todos){
                    localStorage.setItem('todos',JSON.stringify(newTodo))
                }, deep: true
            }
        },
        mounted(){
            this.todos = JSON.parse(localStorage.getItem('todos')) || []
        }, 
        computed:{
            todos_asc(){
                
            }
        }
    }
</script>

