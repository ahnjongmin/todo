<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" v-bind:flagpropsdata="myflag" v-on:flagChangeSignal="flagChange" v-on:removeTodo="removeTodoItem" v-on:changeTodo="changeTodoItem"></TodoList>
    <TodoFooter v-on:removetodoItem="ClearAll"></TodoFooter>
    <!-- changed -->
  </div>
</template>

<script>

import TodoHeader from "./components/TodoHeader.vue"
import TodoInput from "./components/TodoInput.vue"
import TodoList from "./components/TodoList.vue"
import TodoFooter from "./components/TodoFooter.vue"

export default {
  components:{
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter,
  },


  data() {
    return {
      todoItems: [],
      myflag: false,
    }
  },


  created() {
      if(localStorage.length > 0) {
          for (var i = 0; i<localStorage.length; i++) {
              if(localStorage.key(i) == "loglevel:webpack-dev-server")
                  continue;
              this.todoItems.push(localStorage.key(i));
          }
      }
  },


  methods: {
    flagChange(which) {
      this.myflag=which;
    },
    addTodo(todoItem) {
      console.log("oh my god!");
      var temp = localStorage.length;
      localStorage.setItem(todoItem, todoItem);
      console.log(temp, todoItem.length);
      if(temp != todoItem.length) {
        this.todoItems.push(todoItem);
      };
      console.log("oh my god!");
    },
    ClearAll() {
      console.log("OHMYGOD!");
      localStorage.clear();
      this.todoItems=[];
      this.myflag = false;
      console.log("OHMYGOD!");
    },
    removeTodoItem(todoItem, index) {
      console.log("removetodoItem in app.vue");
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    changeTodoItem(before, after, index) {
      console.log("chjangetodoItem in app.vue");
      localStorage.removeItem(before);
      this.todoItems.splice(index, 1);
      localStorage.setItem(after, after);
      this.todoItems.push(after);
      this.myflag = false;
    }
    // changed
  }


}
</script>

<style>
  body{
    text-align: center;
    background-color: #F6F6F8;
  }
  input{
    border-style: groove;
    width: 200px;
  }
  button{
    border-style: groove;
  }
  .shadow{
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
  }
</style>
