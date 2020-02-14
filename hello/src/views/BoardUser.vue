<template>
  <div id="app">
    <h1>Statistics</h1>
    <ul>
      <li v-for="todo of todos" :key="todo.activity">{{todo.activity}}</li>
    </ul>
    <ul>
      <li v-for="todo of todos" :key="todo.time">{{todo.time}}</li>
    </ul>
  </div>
</template>

<script>
import UserService from '../services/user.service';
//import userService from '../services/user.service';
export default {
  name: 'user',
  data() {
    return {
      todos: [],
      todoName: ''
    };
  },


async created() {
    try{
      const res = await UserService.getUserBoard();

      this.todos = res.data;
    }catch(e) {
        UserService.getUserBoard().then(error =>  {
        this.todoName = error.response.data.message;
      })
    }
},



  
};
</script>