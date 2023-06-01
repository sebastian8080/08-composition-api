<template>
  <h1>Pokemon View</h1>
  <h2 v-if="!pokemon && !errorMessage">Loading</h2>
  <h2 v-else-if="errorMessage">{{ errorMessage }}</h2>
  <template v-else>
      <h3>{{ pokemon.name }}</h3>
      <img :src="pokemon.sprites.front_default" :alt="pokemon.name">
      <br>
      <router-link :to="{name: 'pokemon-search'}">Regresar</router-link>
  </template>
</template>

<script>
import { useRoute, onBeforeRouteLeave } from 'vue-router'
import usePokemon from '@/composables/usePokemon'
import { watch } from 'vue'

export default {

    setup(){

        const route = useRoute()

        const { pokemon, isLoading, errorMessage, searchPokemon } = usePokemon(route.params.id)

        watch(
            () => route.params.id,
            () => searchPokemon(route.params.id)
        )

        onBeforeRouteLeave(() => {
            
            const answer = window.confirm('Esta seguro que desea salir')

            if(!answer ) return false

        })

        return{
            pokemon,
            isLoading,
            errorMessage,
        }

    }
}
</script>

<style>

</style>