<template>
    <img class="logo" alt="Aviral Restro Logo" src="../assets/logo2.png">
    <h1> Sign UP </h1>
    <div class="signup">
        <input type="text" v-model="name" placeholder="Enter Name"/>
        <input type="text" v-model="email" placeholder="Enter Email ID"/>
        <input type="password" v-model="password" placeholder="Enter Password" />
        <button v-on:click="signUp">Sign Up</button>
    </div>
    <p>
        If you have already an account then <router-link to="/login">click here to Login</router-link>
    </p>
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
    },
    mounted(){
        let user= localStorage.getItem('user-info');
        if(user)
        {
            this.$router.push({name: 'Home'})
        }
    }
};
</script>