<template>
  <div>
    <NavBar />
    <Footer />
  </div>
</template>

<script>
import Footer from '@/components/Footer.vue';
import NavBar from './components/NavBar.vue';

export default {
  components:{
    Footer,
    NavBar
}
}
</script>>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  margin: 0
}
nav {
  padding: 30px;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  padding: 20px;
  text-transform: uppercase;
}

nav a.router-link-exact-active {
  color: #1d7eec;
}
</style>
