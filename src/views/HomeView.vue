<template>
  <div class="home">
    <HelloWorld msg="Welcome to Home View"/>
    <h2>Suma de dos numeros: {{ num1 + num2 }}</h2>
    <h3>Resultado de una operacion: {{ resultado }}</h3>
    <h5 v-if="!mostrar">Mostrar un elemento solo si una propiedad en particular se establece en true</h5>
    <button @click="hide">hide/unhide</button>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data(){
    return{
      resultado: null,
      mostrar: false,
      num1: 2,
      num2: 2,
    }
  },
  methods:{
    hide(){
      if (this.mostrar === false) {
        this.mostrar = true;
      }else{
        this.mostrar = false
      }
    }
  },
  computed:{
    resultado(){
      return this.num1 + this.num2 *6;
    }
  },
}
</script>
