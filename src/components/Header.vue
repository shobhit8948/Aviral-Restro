<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Restaurant</router-link>
        <a v-on:click="logout">Logout</a>
    </div>
</template>
<script>
export default {
    name: 'Header',
    methods:{
        logout(){
            localStorage.clear();
            this.$router.push({name:'Login'})
        }
    }
}
</script>
<style>
.nav{
    background-color: #000000;
    overflow: hidden;
    cursor: pointer;
}
.nav a{
    float: left;
    color:white;
    padding: 14px 16px;
    text-align: center;
    font-size: 17px;
    text-decoration: none;
    margin-right: 5px;
}
.nav a:hover{
    background-color: white;
    color: black;
}
</style>