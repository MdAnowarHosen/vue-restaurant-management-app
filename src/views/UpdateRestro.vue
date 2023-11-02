<template>
  <div>
    <h1>Update Restaurant</h1>
    <div class="restro">
      <input type="text" v-model="name" placeholder="Restaurant Name" />
      <input type="text" v-model="address" placeholder="Restaurant Address" />
      <input type="text" v-model="contact" placeholder="Restaurant Contact" />
      <button v-on:click="Update()">Update</button>


    </div>
  </div>
</template>
  
<script>
import axios from "axios";
export default {
  name: "UpdateRestro",
  data() {
    return {
      name: '',
      address: '',
      contact: '',
    };

  },

  methods: {
    async getRestaurant() {

      let results = await axios.get("http://localhost:3000/restaurant/" + this.$route.params.id);

      if (results.status == 201 || results.status == 200) {
        this.name = results.data.name;
        this.address = results.data.address;
        this.contact = results.data.contact;
      } else {
        alert("Failed to get restaurant data");
      }

    },

    async Update() {

      let results = await axios.put("http://localhost:3000/restaurant/"+ this.$route.params.id, {
        name: this.name,
        address: this.address,
        contact: this.contact,
      });

      if (results.status == 201 || results.status == 200) {
        alert("Restaurant updated successfully");
      } else {
        alert("Failed to update restaurant");
      }

    }
  },
  async mounted() {

    // get restaurant
    this.getRestaurant();


    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "login" });
    }
  },
};
</script>
  


  