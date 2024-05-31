<template>
    <img class="logo" alt="Aviral Restro Logo" src="../assets/logo2.png">
    <h1> Sign UP </h1>
    <div class="signup">
        <input type="text" v-model="name" placeholder="Enter Name"/>
        <input type="text" v-model="email" placeholder="Enter Email ID"/>
        <input type="password" v-model="password" placeholder="Enter Password" />
        <button v-on:click="signUp">Sign Up</button>
    </div>
</template>
<script>

import axios from 'axios'
export default {
    name : 'SignUp',
    data(){
        return{
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
        async signUp(){
            {
                let result = await axios.post("http://localhost:3000/users",{
                    email:this.email,
                    name: this.name,
                    password: this.password
                });
                console.warn(result);
                if(result.status==201){
                    alert("Sign-up done")
                    localStorage.setItem("user-info",JSON.stringify(result.data))
                    this.$router.push({name:'Home'})
                }
            }
        }
    }
}
</script>
<style>
.logo{
    width: 100px;
}
.signup input{
    width: 300px;
    height: 30px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 2px solid black;
}
.signup button{
    color: white;
    background-color: black;
    margin: 1%;
    width: 300px;
    height: 30px;
    border-radius: 15px;
    cursor: pointer;
}
</style>