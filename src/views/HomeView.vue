<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>Hello, {{ name }}</h1>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  data()
  {
    return{
      name: '',
    }
  },
  components: {
    HelloWorld
  },
 
  mounted(){
        let user = localStorage.getItem('user-info');
        this.name = JSON.parse(user).name;
        if(!user)
        {
            this.$router.push({name:"login"});
        }
    },
}
</script>
