<template>
  <div class="pokemon-stat">
    <li>
      <span class="stat-name">
        <b>{{ item.stat.name }} = {{ item.base_stat }}</b>
      </span>
    </li>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
@Component({
  name: "Stat",
})
export default class Stats extends Vue {
  @Prop({ default: [] }) public item!: [];
}
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,400;1,700&display=swap");
.pokemon-stat {
  // margin-top: 10px;
  text-decoration: underline wavy red;
  text-decoration-thickness: 3px;
  padding: 10px;

  > li {
    list-style-type: none;
    background: linear-gradient(
      to bottom,
      #41ffab,
      #41ffab 60%,
      #18d9ff 70%,
      #18d9ff 100%
    );
    background-clip: text;
    font-size: xx-large;
    -webkit-background-clip: text;
    color: transparent;
    background-repeat: no-repeat;
    transition: background 0.2s ease-out;
    white-space: nowrap;
    text-align: left;
  }
}
</style>