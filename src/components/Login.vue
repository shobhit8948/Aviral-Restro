<template>
    <img class="logo" alt="Aviral Restro Logo" src="../assets/logo2.png">
    <h1> Login </h1>
    <div class="login">
        <input type="text" v-model="email" placeholder="Enter Email ID"/>
        <input type="password" v-model="password" placeholder="Enter Password" />
        <button v-on:click="login">Login</button>
    </div>
    <p>
        If you don't have an account then <router-link to="/sign-up">click here to Sign Up</router-link>
    </p>
</template>
<script>
import axios from 'axios'

export default{
    name: 'Login',
    data(){
        return{
            email:'',
            password:''
        }
    },
    methods:{
        async login()
        {
            let result = await axios.get(
                `http://localhost:3000/users?email=${this.email}&password=${this.password}`
            )
            if(result.status==200 && result.data.length>0){
                localStorage.setItem("user-info",JSON.stringify(result.data[0]))
                this.$router.push({name:'Home'})
            }
            console.warn(this.email,this.password)
        }
    }
};
</script>
