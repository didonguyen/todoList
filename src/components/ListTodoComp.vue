<template>
  <div class="wrapper-todo-list">
      <ul class="todo-list">
          <li 
            v-for="(item, index) in todoList"
            v-bind:key="index"
          >
            <p>{{ item.todo }}</p>
            <div class="button">
                <button class="update-button" v-on:click="handleClickUpdate(index)">Update</button>
                <button class="delete-button" v-on:click="$emit('deleteTodo', index)">Delete</button>
            </div> 
          </li>
      </ul>
  </div>
</template>

<script>
import TodoComp from './TodoComp';
export default {
  name: 'ListTodoComp',
  props: {
      popupUpdate: { type: Boolean, default: false}
  },
  data () {
      return {
          
      }
  },
  props: {
      todoList: { type: Array, default: [] }
  },
  components: {
      TodoComp
  },
  computed: {
      
  },
  methods: {
      handleClickUpdate(index){
        this.$emit('clickUpdateEvent', index);
      }
  }

};
</script>

<style>
.wrapper-todo-list{
    width: 90%;
    margin: 5px 5%;
}
.todo-list{
    
    padding: none;
    margin-left: 10px 10px;
    width: 100%;
    list-style-type: none;
    
}
.todo-list li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    border: 1px solid #000;
    border-radius: 4px;
    padding: 5px 8px;
    margin-bottom: 5px;
    background-color: rgb(243, 245, 244);
    font-size: 18px;
}
.update-button{
    border: 1px solid rgb(57, 158, 189);
    width: 80px;
    height: 45px;
    background-color: rgb(203, 214, 228);
    color: rgb(5, 5, 5);
    border-radius: 4px;
    font-size: 18px;
    transition: all .3s ease;
}
.update-button:hover{
    border: 1px solid rgb(57, 158, 189);
    background-color: #333;
    color: #fff;
}
.delete-button{
    border: 1px solid rgb(175, 175, 209);
    width: 80px;
    height: 45px;
    background-color: rgb(231, 203, 202);
    color: rgb(5, 5, 5);
    border-radius: 4px;
    font-size: 18px;
    transition: all .3s ease;
}

.delete-button:hover{
    border: 1px solid rgb(57, 158, 189);
    background-color: #333;
    color: #fff;
}

@media only screen and (max-width: 480px){
    .wrapper-todo-list{
        width: 100%;
        margin: 5px 5%;
    }
    .todo-list{  
        padding: none;
        margin-left: 10px 10px;
        width: 100%;
        list-style-type: none;
    }
.todo-list li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    border: 1px solid #000;
    border-radius: 4px;
    padding: 5px 8px;
    margin-bottom: 5px;
    background-color: rgb(243, 245, 244);
    font-size: 22px;
    }
}
</style>
