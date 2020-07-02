<template>
  <div id="app">
    <h1>Todo List</h1>

    <add-comp v-bind:todoList="todoList"/>

    <list-todo-comp 
      v-bind:todoList="todoList"
      v-on:deleteTodo="deleteTodo"
      v-on:clickUpdateEvent="clickUpdateEvent"
      v-bind:popupUpdate="popupUpdate"
    />

    <update-comp 
      v-bind:todoList="todoList"
      v-bind:index="indexUpdate"
      v-bind:popupUpdate="popupUpdate"
      v-on:UpdateTodoList="UpdateTodoList"
    />

  </div>
</template>

<script>
import AddComp from './components/AddComp';
import ListTodoComp from './components/ListTodoComp';
import UpdateComp from './components/UpdateComp';

export default {
  name: 'app',
  data () {
    return {
      todoList: [
        { id: 100, todo: 'Wake Up' },
        { id: 101, todo: 'Exercise' },
        { id: 102, todo: 'Take Shower' },
        { id: 103, todo: 'Have Breakfast' },
        { id: 104, todo: 'Go to Work' }
      ],
      popupUpdate: false,
      indexUpdate: -1
    }
  },
  components: {
    AddComp,
    ListTodoComp,
    UpdateComp
  },
  methods: {
    deleteTodo(index){
      this.todoList.splice(index, 1);
    },
    clickUpdateEvent(index){
      this.indexUpdate = index;
      this.popupUpdate = true;
    },
    UpdateTodoList(newUpdate){
      let updateIndex = newUpdate.updateIndex;
      let newtodo = newUpdate.newUpdate;
      this.$set(this.todoList, updateIndex, {id: 100 + updateIndex, todo: newtodo})
      this.popupUpdate = false;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
