<template>
  <div class="todo-item" :class="{'is-completed':todo.completed}">
    <p class="">
      <input type="checkbox" v-on:change='markComplete'>
      {{todo.title}}
    <button class="del" @click="$emit('del-todo',todo.id)">X</button>
  </p>

  </div>

</template>
<script>

export default{
  name : 'TodoItem',
  props : ['todo'],
  methods :{
    markComplete(){
      this.todo.completed = !this.todo.completed;

    }
  }

}

</script>
<style scoped>
.todo-item{
  background: #f4f4f4;;
  padding: 10px;
  border-bottom: 1px #ccc solid;
}

  .is-completed{
    text-decoration: line-through;
  }
  .del{
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    float: right;
    border-radius: 50%;
    cursor: pointer;
  }
</style>
