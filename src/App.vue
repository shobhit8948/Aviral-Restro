<template>
  <router-view />
</template>

<script>
export default {
  name: 'App', 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
body{
  padding: 0%;
  margin: 0%;
}
.logo{
  margin-top: 60px;
  width: 100px;
}
.login input, .signup input{
    width: 300px;
    height: 30px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 2px solid black;
}
.login button, .signup button{
    color: white;
    background-color: black;
    margin: 1%;
    width: 300px;
    height: 30px;
    border-radius: 15px;
    cursor: pointer;
}
</style>
