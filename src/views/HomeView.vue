<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>Hello, {{ name }}</h1>
    <h2>All Restaurants</h2>

    <div class="restro-table">
      <table>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Address</th>
          <th>Contact</th>
          <th>Action</th>
        </tr>
        <tr v-for="restaurant in restaurants" :key="restaurant.id">
          <td>{{ restaurant.id }}</td>
          <td>{{ restaurant.name }}</td>
          <td>{{ restaurant.address }}</td>
          <td>{{ restaurant.contact }}</td>
          <td class="action">
            <RouterLink :to="'/update/restaurant/'+restaurant.id">Edit</RouterLink>
            <a href="#">Delete</a>
          </td>
        </tr>
  
      </table>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from "axios";

export default {
  name: 'HomeView',
  data() {
    return {
      name: '',
      restaurants: [],
    }
  },
  components: {
    HelloWorld
  },

  async mounted() {
    let user = localStorage.getItem('user-info');
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "login" });
    }

    // get restaurants
    await this.getRestro();


  },

  methods:
  {
    async getRestro() {

      let results = await axios.get("http://localhost:3000/restaurant");

      if (
        (results.status == 201 || results.status == 200) &&
        results.data.length > 0

      ) {
        this.restaurants = results.data;
        console.warn(results.data);
      }
    }
  }

}
</script>

<style>
.restro-table {
  width: 90%;
  margin: auto;
}

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
.action a{
  margin: 0 5px;
  background-color: rgb(83, 82, 82);
  color:aliceblue;
  padding: 5px 10px;
  border-radius: 5px;
  text-decoration: none;
}
.action a:hover{
  background-color: rgb(56, 55, 55);
}
</style>