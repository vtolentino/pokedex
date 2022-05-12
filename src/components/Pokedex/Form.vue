<template>
  <div class="form container" v-on:submit.prevent="emmitSearch($event)">
    <form class="form-control">
      <input
        type="text"
        class="form-control in-txt in-txt--primary"
        placeholder="Search Pokemon"
        required
        v-model="pokemonId"
      />
      <span class="in-btn in-btn--tag"></span>
      <span class="in-btn in-btn--tag secundary"></span>
      <input
        type="submit"
        class="form-control in-btn in-btn--primary float-right"
        value="OK"
      />
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
@Component({
  name: "PokedexForm",
})
export default class PokedexForm extends Vue {
  //   @Prop() public pokemon!: any;
  //   @Prop({ default: false }) public error!: boolean;
  //   @Prop({ default: false }) public loading!: boolean;
  pokemonId: string | number = "";

  data() {
    return {};
  }

  emmitSearch(event: string) {
    this.$emit("pato", { pokemonId: this.pokemonId.toString().toLowerCase() });
    // console.log(event)
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.screen {
  background-image: url("../../assets/images/glitch-static.gif");
  width: 400px;
  height: 300px;
  margin: 0 auto;
  margin-top: 10px;
}

.container {
  width: 80%;
  margin: 0 auto;
  margin-top: 30px;
  height: auto;
}

.in-txt {
  width: 300px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  height: 30px;

  &--primary {
    color: currentColor;
    background-color: #ffe300;
    border-radius: 14px;
    box-shadow: 6px 6px;
    font-size: x-large;
    border: 10px solid;
    height: 60px;
    text-transform: uppercase;
    padding: 0 50px;
    display: inherit;
    transition: margin 0.15s ease-in-out;
  }

  &--primary:focus {
    background-color: yellow;
    border: 10px solid #000;
    outline: none;
    margin: 0 0 10px -12px;
    transition: margin 0.15s ease-in-out;
  }
}

.in-btn {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  height: 30px;

  &--primary {
    color: #3d0f53;
    margin-top: 30px;
    background-color: #00a9f6;
    border-radius: 140px;
    box-shadow: 6px 6px #000;
    font-size: xx-large;
    font-weight: bold;
    position: relative;
    border: 10px solid;
    height: 60px;
    text-transform: uppercase;
    padding: 29px 24px 69px 23px;
    position: relative;
    transition: margin 0.15s ease-in-out;

    &:hover {
      cursor: pointer;
      color: #000;
      background-color: #00dafe;
    }

    &:checked {
      color: yellow;
    }
  }

  &--tag {
    color: #3d0f53;
    margin-top: 30px;
    background-color: #2ff555;
    border-radius: 140px;
    box-shadow: 6px 6px #000;
    font-size: xx-large;
    font-weight: bold;
    position: relative;
    border: 10px solid;
    height: 60px;
    text-transform: uppercase;
    padding: 0px 0px 0px 100px;
    position: relative;
    transition: margin 0.15s ease-in-out;
    position: relative;
    top: 40px;
    margin: 5px;

    &.secundary {
      background-color: #ff651b;

      &:hover {
        background-color: red;
      }
    }

    &:hover {
      cursor: pointer;
      color: #000;
      background-color: #05ff34;
    }

    &:checked {
      color: yellow;
    }
  }

  &.float-right {
    float: right;
  }
}
</style>