<template>
  <form class="additem" action="" method="post" @submit ='addTodo'>
    <input type="text" v-model="title" name="title" placeholder="Add To Do"/>
    <input type="submit" value="Add"/>

  </form>

</template>
<script>
//import uuid from 'uuid';
export default{
  name: 'AddTodo',
  data(){
    return{
    title:''
  }
  },
  methods :{
    addTodo (e){
      e.preventDefault();
      const newTodo={
        //id: uuid.v4(),
        title:this.title,
        completed:false
      }
      //send up to parent
      this.$emit('add-todo', newTodo);
      this.title =''
    }
  }
}

</script>

<style scoped>

  .additem{
    background: #ddd;
    display: flex;
    padding: 15px
  }
  input[type='text']{
    padding: 10px;
    flex:10;

  }
  input[type='submit']{
    flex: 2;

  }
</style>
