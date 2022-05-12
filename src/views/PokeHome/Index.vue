<template>
    <div>
        <pokedex></pokedex>
    </div>
</template>

<script lang="ts">

import { Vue ,Component } from "vue-property-decorator"
import Pokedex from "@/components/Pokedex/Index.vue"

@Component({
    components:{
        Pokedex
    }
})
export default class PokeHome extends Vue {
    
}

</script>

<style scoped>

</style>