<template>
    <h1>Sign Up</h1>
    <img alt="Vue logo" src="../assets/restro-logo.jpg" width="100">
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name" />
        <input type="email" v-model="email" placeholder="Enter Email" />
        <input type="password" v-model="password" placeholder="Enter Password" />
        <button v-on:click="signUp">Signup</button>
        <p><router-link to="/login" >Login</router-link></p>

    </div>
</template>
  
<script>
import axios from "axios";
export default {
    name: "SignUp",
    data() {
        return {
            name: "",
            email: "",
            password: "",
           
            
        };
        
    },

    methods: {
        async signUp() {
            console.warn("ok", this.name, this.email, this.password);

            let results = await axios.post("http://localhost:3000/users", {
                name: this.name,
                email: this.email,
                password: this.password,
            });

            if (results.status == 201) {
                //   alert("Signup successful");
                console.warn(results);

                localStorage.setItem('user-info', JSON.stringify(results.data));
                this.$router.push({ name: "home" });
            } else {
                alert("Failed Signup");
            }


        },
    },
    mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "home" });
    }
  },
};
</script>
  

  