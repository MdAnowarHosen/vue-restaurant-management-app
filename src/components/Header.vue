<template>
    <div class="nav">
        <ul>
            <li><router-link to="/">Home</router-link></li>
            <li><router-link to="/about">About</router-link></li>
            <li><a to="#">Contact</a></li>
            <li v-show="loggedIn"><router-link to="/add/restaurant">Add Restaurant</router-link></li>
            <li v-show="!loggedIn"><router-link to="/sign-up">Register</router-link></li>
            <li v-show="!loggedIn"><router-link to="/login">Login</router-link></li>
            <li v-show="loggedIn"><a href="#" v-on:click="logout()">Logout</a></li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            loggedIn: '',
        };
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        console.warn(user);
        if (user) {
            this.loggedIn = true;
        }
        else {
            this.loggedIn = false;
        }

    },
    methods:
    {
        logout() {
            let logout = localStorage.removeItem('user-info');
            this.loggedIn = false;
            this.$router.push({ name: "login" });

        }
    }
}
</script>

<style lang="scss" scoped>
.nav ul {

    list-style-type: none;
    background-color: rgb(94, 94, 94);
    padding: 15px 0;
    font-size: 23px;

}

.nav ul li {
    padding: 5px;
    display: inline;


}

.nav ul li a {
    padding: 5px;
    text-decoration: none;
    color: aliceblue;

}

.nav ul li a:hover {
    background-color: rgb(46, 46, 46);
}
</style>