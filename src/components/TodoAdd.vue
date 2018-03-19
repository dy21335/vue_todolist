<template>
  <div id="addToDo">
    <input type="text" name="" value="" v-model="todo"
           @keyup.enter="addTodo"/>
    <button type="button" @click="addTodo">Add</button>
  </div>
</template>


<script>
  export default {
    name: 'addTodo',
    data: () => ({
      todo: ''
    }),
    methods: {
      addTodo(){
        if(this.todo){
          this.$emit('add',this.todo);
          this.todo=''
        }
        else{
          alert("you have added nothing!");
        }
      }
    }
  };
</script>

<style scoped>
.input{
  max-width: 200px;
}
</style>
