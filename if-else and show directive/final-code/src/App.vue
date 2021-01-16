<template>
  <div id="app-content">
    
         <Login />
  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld.vue";
import Login from "./components/Login.vue";

export default {
  name: "App",
  components: {
    //HelloWorld,
    Login,
  },
};
</script>

<style>
#app-content{
  margin-top:17vh;
}
/* #app-content {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
