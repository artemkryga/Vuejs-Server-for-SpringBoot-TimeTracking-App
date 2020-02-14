<template>
 <div id="app">
   <h1>Daily activities</h1>
   <template>
  <div>
     <b-table striped hover :items="todos">
        <li v-for="fruit in todos" :key="fruit">{{fruit}}</li>
     </b-table>
  </div>
</template>
 </div>
</template>

<script>
import UserService from '../services/user.service';

export default {
  name: 'all',
  data() {
    return {
      todos: [],
      todoName: ''
    };
  },


async created() {
    try{
      const res = await UserService.getPublicContent();

      this.todos = res.data;
    }catch(e) {
        UserService.getPublicContent().then(error =>  {
        this.todoName = error.response.data.message;
      })
    }
},



  
};
</script>