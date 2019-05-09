<template>
  <div id="app">
    <GitUser user="klementj"></GitUser>
    <NotificationMessage v-if="TestingError" message="flere repos end 10" colorCode="alert-danger" />
  </div>
</template>

<script>
import GitUser from './components/GitUser'
import NotificationMessage from './components/NotificationMessage'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'app',
  components: {
    GitUser,
    NotificationMessage,
    BootstrapVue
  },
  data: function() {
    return{
      TestingError: false,
    }  
  }, 
 mounted: function(){
    this.TooManyRepo()
  },
  methods: {
    TooManyRepo: function(){
      10 ? this.TestingError = false : this.TestingError = true
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
