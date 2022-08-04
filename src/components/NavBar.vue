<template>
    <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
    </nav>
  <router-view/>
</template>

<script>
export default {

}
</script>

<style>
nav{
    background-color: rgb(207, 207, 207);
}


</style>