<template>
    <div>
      <Header />
      <h1>
        Hello {{ name }}, Welcome on Home Page
      </h1>
      <table border="1">
        <thead>
          <tr>
            <th>Id</th>
            <th>Name</th>
            <th>Contact</th>
            <th>Address</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in restaurant" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contact }}</td>
            <td>{{ item.address }}</td>
            <td><router-link :to="'/update/'+item.id">Update</router-link>
            <button v-on:click="deleteRestaurant(item.id)">Delete</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import Header from './Header.vue';
  
  export default {
    name: 'Home',
    data() {
      return {
        name: '',
        restaurant: [],
      };
    },
    components: {
      Header
    },
    methods:{
        async deleteRestaurant(id){
            let result = await axios.delete("http://localhost:3000/restaurant/"+id);
            console.warn(result)
            if(result.status==200){
                this.loadData()
            }
        },
        async loadData(){
            let user= localStorage.getItem('user-info');
            this.name=JSON.parse(user).name;
            if(!user){
                this.$router.push({name:'SignUp'})
            }
            let result=await axios.get("http://localhost:3000/restaurant");
            this.restaurant=result.data;
        }
    },

    async mounted() {
      this.loadData();      
    }
  };
  </script>
<style>
td{
    width:340px;
    height: 40px;
}</style>