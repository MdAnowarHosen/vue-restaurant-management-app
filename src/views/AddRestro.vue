<template>
   <div>
    <h1>Add Restro</h1>

   </div>

</template>
  
<script>
import axios from "axios";
export default {
    name: "AddRestro",
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
  


  