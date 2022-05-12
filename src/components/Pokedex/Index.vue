<template>
  <div class="pokedex">
    <div class="pokedex-left">
      <div class="pokedex-screen-container">
        <Screen  :pokemon="pokemon" :loading="loading" :error="error" />
      </div>
      <div class="pokedex-left-botton">
        <Form @pato="hangleSubmit($event)"/>
      </div>
    </div>
    <div class="pokedex-right">
      <Stats  :pokemon="pokemon" :loading="loading" :error="error" />
    </div>
  </div>
</template>
<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

import Form from "@/components/Pokedex/Form.vue";
import Screen from "@/components/Pokedex/Screen.vue";
import Stats from "@/components/Pokedex/Stats.vue";
import { getPokemonById } from "@/api";

@Component({
  components: {
    Form,
    Screen,
    Stats,
  },
})
export default class Pokedex extends Vue {
  public error: boolean = false;
  public loading: boolean = false;
  public pokemon: [] = [];
  public pokemonId: string | number = "";

  data() {
    return {
      error: false,
      loading: false,
      pokemon: [],
      pokemonId: Math.floor(Math.random() * 806 + 1),
    };
  }
  public async fetchPokemon() {
    this.loading = true;
    getPokemonById(this.pokemonId)
      .then((res) => res.json())
      .then((data) => {
        this.pokemon = data;
        console.log(data)
        this.loading = false;
      })
      .catch((err) => {
        this.loading = false;
        this.error = true;
        console.log({ err });
      });
  }
  created() {
    this.fetchPokemon();
  }
  hangleSubmit(event: string){
      if( event !== ""){
          this.error = false;
          this.pokemonId = event.pokemonId;
          this.fetchPokemon();
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.pokedex {
  background-color: #41ffab;
  padding-top: 70px;
  padding-bottom: 70px;
  text-align: -webkit-center;
}

.pokedex-left {
  background-color: #ff1a55;
  background-image: url("../assets/logo.png");
  background-size: 150px;
  background-repeat: no-repeat;
  background-position: 3% 97%;
  width: 600px;
  height: 850px;
  margin: 0 auto;
  border-radius: 10px;
  text-align: center;
  border: 10px solid #3d0f53;
  box-shadow: 25px 30px #000;
  display: inline-block;
}

.pokedex-right {
  background-color: #ff1a55;
  width: 600px;
  height: 850px;
  margin: -10px;
  border-radius: 10px;
  text-align: center;
  border: 10px solid #3d0f53;
  box-shadow: 25px 30px #000;
  display: inline-block;
  transform: rotate3d(-2, 42, 0, 26deg);
}

.form.container {
  background-color: #ff1a55;
}

.pokedex-screen-container {
  padding-top: 20px;
}
</style>