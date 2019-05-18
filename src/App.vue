<template>
  <div id="app">
    <Header/>
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header'
export default{
  name       : 'app',
  components : {
    Header
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
