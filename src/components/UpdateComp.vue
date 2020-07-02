<template>
  <div class="wrapper-update" v-bind:class="getClassPopup">
      <div class="update-area">
          <div class="old">
            <h3>Old To do: {{ index == -1 ? null : todoList[index].todo }}</h3>
          </div>
          <div class="new">
            <h3>New To Do: </h3>
            <input type="text" id="new-update" v-model="newUpdate">
            <button v-on:click="handleUpdate">Update</button>
          </div>
          
      </div>

  </div>
</template>

<script>
export default {
  name: 'UpdateComp',
  props: {
      todoList: { type: Array, default: [] },
      popupUpdate: { type: Boolean, default: false},
      index: { type: Number, default: -1}
  },
  data() {
      return {
          newUpdate: ''
      }
  },
  computed: {
      getClassPopup(){
          return {
              'open-popup': this.popupUpdate 
          }
      }
  },
  methods:{
      handleUpdate() {
          let newUpdate = {
              newUpdate: this.newUpdate,
              updateIndex: this.index
          }
          this.$emit('UpdateTodoList', newUpdate);

      }
  }
};
</script>

<style>
.wrapper-update{
    position: fixed;
    background-color: rgba(0, 0, 0, 0.4);
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    opacity: 0;
    visibility: hidden;
    transition: all .3s ease;
}
.wrapper-update.open-popup{
    opacity: 1;
    visibility: visible;
}
.update-area{
    display: flex;
    flex-direction: column;
    width: 500px;
    padding: 30px;
    background-color: #fff;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-family: Arial, Helvetica, sans-serif;
}
.old{
    display: flex;
    align-items: center;
    justify-content: left;
}
.new{
    display: flex;
    align-items: center;
    justify-content: left;
}
.new input{
    height: 30px;
    flex-grow: 1;
    margin: 0px 15px;
    padding: 0 5px;
    font-size: 18px;
}
.new button{
    border: 1px solid rgb(57, 158, 189);
    width: 80px;
    height: 35px;
    background-color: rgb(203, 214, 228);
    color: rgb(5, 5, 5);
    border-radius: 4px;
    font-size: 18px;
}
.new p{
    font-size: 18px;
}
</style>
