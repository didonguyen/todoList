<template>
  <div class="add-new">
      <h3>Add a new todo: </h3>
      <input v-model="todo" type="text" placeholder="Do Something..." id="add-new">
      <button class="add-button" v-on:click="handleAddNew">Add</button>
    </div>
</template>

<script>
export default {
  name: 'AddComp',
  props: {
      todoList: { type:Array, default: [] }
  },
  data() {
      return {
          todo: ''
      }
  },
  methods: {
      handleAddNew(){

          let objTodo = { key: 100 + this.todoList.length, todo: this.todo}
          this.todoList.push(objTodo);
      }
  }
};
</script>

<style>
.add-button{
    border: 1px solid rgb(72, 197, 93);
    width: 80px;
    height: 35px;
    background-color: rgb(212, 235, 212);
    color: rgb(5, 5, 5);
    border-radius: 4px;
    font-size: 18px;
}
.add-new{
    width: 100%;
    display: flex;
    justify-content: left;
    align-items: center;
}
.add-new input{
    height: 30px;
    flex-grow: 1;
    margin: 0px 15px;
    padding: 0 5px;
    font-size: 18px;
}
</style>
