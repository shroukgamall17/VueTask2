<template>
  <div class="container my-1">
    <navbar/>
  <div class="row justify-content-between my-2">
    <links/>
    <studentTable/>
  </div>
  <theForm/>
  </div>
   <br><br><br><br>
   
   <foot/>
</template>

<script>
import navbar from './components/navbar.vue'
import studentTable from './components/table.vue'
import links from './components/links.vue'
import theForm from './components/form.vue'
import foot from './components/foot.vue'



export default {
  name: 'App',
  components: {
   links,studentTable,navbar,theForm,foot
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
