<template>
  <div id="app">
    <div v-for="(poke, index) in pokemons" :key="index">
    <Pokemon :name="poke.name" :url="poke.url" :num="index+1"/>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Pokemon from "./components/Pokemon";
export default {
  name: 'App',
  data(){
    return{
      pokemons: []
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res => {
      console.log("Pegou a lista de pokemons");
      this.pokemons = res.data.results;
    })
  },
 components: {
   Pokemon
 }
}
</script>

<style>

</style>
