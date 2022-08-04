<template>
  <div  :class="[isActive ? lightClass : darkClass]">
    <div class="modo-container">
      <button @click="lightMode">🌞</button>
      <button @click="darkMode">🌚</button>
    </div>
    <h1>This is an About page</h1>
    <div v-if="loading"> <!--3.Estado de loading para cuando los datos se estan cargando.-->
      <h2>cargando</h2>
    </div>
    <div v-if="error">
      {{ error }}
    </div>
    <div  class="films" v-if="data">
      <div class="film" v-for="film in data.results" :key="film.url"> <!--la url la utilizare como identificador unico -->
        <div>
          <h1>{{film.title}}</h1>
          <p>{{ film.director }}</p>
          <p>{{film.release_date.split("-",1).join()}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "home",
  data() {
    return {
      data: null,
      loading: false,//1.Estado de loading para cuando los datos se estan cargando.
      error: "",
      isActive: true,
      lightClass: "light",
      darkClass: "dark",
    };
  },
  methods: {
      //CON AXIOS ASYNC AWAIT
      async getFilms(){
        this.loading = true;//2.Estado de loading para cuando los datos se estan cargando.
        try{
        const {data} = await axios ("https://swapi.dev/api/films/");
        this.data = data;
        }catch (error){
          this.error = error;
        }finally{
          this.loading = false;
        }
      },
      getId(url) {
        return url.split("/").reverse()[1];
      },
      darkMode(){
        if (this.isActive === true) {
          this.isActive = false;
        };
      },
      lightMode(){
        if (this.isActive === false) {
          this.isActive = true;
        };
    },
    },
    mounted() {//Realiza una accion automática, sin necesidad de un evento. Que en este caso sera el método getFilms
      this.getFilms()
    },
};
</script>
<style>
  .modo-container{
    display: flex;
    justify-content: right;
    gap: 25px;
  }
  .films{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 25px;
  }
  .film{
    border: solid 1px rgb(180, 212, 224);
  }
  .light{
    background-color: white;
    color: black;
  }
  .dark{
    background-color: black;
    color: white;
  }
  button{
    background-color: transparent;
    font-size: 2rem;
    border: none;
  }
</style>