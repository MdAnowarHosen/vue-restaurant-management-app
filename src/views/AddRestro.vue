<template>
  <div>
    <h1>Add Restro</h1>
    <div class="restro">
      <input type="text" v-model="name" placeholder="Restaurant Name" />
      <input type="text" v-model="address" placeholder="Restaurant Address" />
      <input type="text" v-model="contact" placeholder="Restaurant Contact" />
      <button v-on:click="Add()">Add</button>


    </div>
  </div>
</template>
  
<script>
import axios from "axios";
export default {
  name: "AddRestro",
  data() {
    return {
      name: '',
      address: '',
      contact: '',
    };

  },

  methods: {
    async Add() {

      let results = await axios.post("http://localhost:3000/restaurant", {
        name: this.name,
        address: this.address,
        contact: this.contact,
      });

      if (results.status == 201) {
        alert("Restaurant added successful");
          this.name = '';
          this.address = '';
          this.contact = '';
      } else {
        alert("Failed to add restaurant");
      }

    }
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "login" });
    }
  },
};
</script>
  


  