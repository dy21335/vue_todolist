<template>
  <div id="todoList">
    <todo-add v-on:add="addTodo"></todo-add>
    <h1>To Do List</h1>
    <ul class="todos">
    <li v-for="todo,index in todos" class="todo">
      <input type="checkbox" name="" value="" :checked="todo.isCompleted"
             @click="completed(index)" />
      <span :class="todo.isCompleted?'completed':''" @click="completed(index)"><em>{{index+1}}.</em>{{todo.text}}</span>
    </li></ul>
    <div>
      <p v-show="todos.length == completedCounts">
        Congratulations?You have done everything!
      </p>
      <p v-show="todos.length != completedCounts">
        You have <strong>{{todos.length}}</strong> things to do.
        {{completedCounts}} have done and {{notCompletedCounts}} have to be done.
      </p>
    </div>
  </div>

</template>

<script>
  import TodoAdd from './TodoAdd.vue'
  export default {
    name:'TodoList',
    components:{
      TodoAdd
    },
    data: () => ({
      todos:[{
        text:'eat',
        isCompleted:false
        },
          {
            text:'sleep',
            isCompleted:false
        }]
      }),
      methods: {
        completed(index) {
          this.todos[index].isCompleted = !this.todos[index].isCompleted
        },
        addTodo(todo){
          this.todos.push({
            text:todo,
            isCompleted:false
          })
        }
      },
    computed:{
      completedCounts(){
        return this.todos.filter(item=>item.isCompleted).length;
      },
      notCompletedCounts(){
        return this.todos.filter(item=>!item.isCompleted).length;
      }
    }
    };

</script>

<style>
#todoList{
  margin: 0 auto;
  max-width: 350px;
}
  .todos li{
    list-style: none;
  }
  .todo{
    text-align: left;
    cursor: pointer;
  }
  .completed{
    text-decoration: line-through;
  }

</style>
