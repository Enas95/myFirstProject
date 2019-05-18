<template>
  <div id="app">
    <Header/>
    <AddToDo v-on:add-todo='addTodo'/>
    <Todos v-bind:todos='todos' v-on:del-todo="deleteTodo"/>

  </div>
</template>

<script>
//import new components
//import Header from '../components/layout/Header';
import Todos from '../components/Todos';
import AddToDo from '../components/AddToDo';
import axios from 'axios';


export default {
  name: 'home',
  components: {
    //Header,
    AddToDo,
    Todos


  },
  data (){
    return {
      //array of objects
      todos:[
        /*{
          id        : 1,
          title     : 'Course vueJs',
          completed : false
        },
        {
          id        : 2,
          title     : 'Course Sass',
          completed : true
        },
        {
          id        : 3,
          title     : 'Git & Github',
          completed : false
        }*/
      ]
    }
  },
  methods :{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
            .then(res=>this.todos = this.todos.filter(todo=> todo.id !== id))
            .catch(err=> alert(err));
      //this.todos = this.todos.filter(todo=> todo.id !== id)

    },
    addTodo(newTodo){
      const {title,completed} = newTodo;
      //this.todos =[...this.todos, newTodo]
      axios.post('https://jsonplaceholder.typicode.com/todos',{title,completed})
            .then(res=>this.todos =[...this.todos, res.data])
            .catch(err=> alert(err));

    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
         .then(res => this.todos = res.data)
         .catch(err => alert(err));

  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body{
  font-family: Arial,Helvetica,sans-serif;
  line-height: 1.4;
}
</style>
