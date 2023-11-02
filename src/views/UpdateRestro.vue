<template>
  <div>
    <h1>Update Restro</h1>
   </div>

</template>
  
<script>
import axios from "axios";
export default {
    name: "UpdateRestro",
    data() {
        return {
      
           
            
        };
        
    },

    methods: {

    },
    mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "login" });
    }
  },
};
</script>
  

  