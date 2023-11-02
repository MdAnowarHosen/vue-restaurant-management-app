<template>
  <Header/>
  <router-view/>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
  },
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  margin: 0;
  padding: 0;
}


.register input, .restro input {
    width: 300px;
    height: 50px;
    padding-left: 20px;
    display: block;
    margin-bottom: 25px;
    margin-left: auto;
    margin-right: auto;
    border: 2px solid #db991d;
}

.register button, .restro button {
   
    height: 40px;
    border: 2px solid #db991d;
    background: #db991d;
    padding: 10px 140px;
    border-radius: 5px;
}
</style>




