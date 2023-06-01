<template>
  <h1>Buscar Pokemon: {{ pokemonId }}</h1>
  <form @submit.prevent="onSubmit">

      <input v-model="pokemonId" type="number" placeholder="Numero de pokemon" ref="searchTxtId">

  </form>
  <br>
  <span>Presione enter para buscar</span>
</template>

<script>
import { ref, onActivated } from 'vue'
import { useRouter } from 'vue-router'

export default {

    setup(){

        const pokemonId = ref(1)
        const router = useRouter()
        const searchTxtId = ref()

        onActivated( () => {
            searchTxtId.value.select()
        })

        return{
            pokemonId,
            searchTxtId,
            
            onSubmit: () => {
                console.log('pokemon a buscar ', pokemonId.value )
                router.push({ name: 'pokemon-id', params: {id: pokemonId.value}})
            }
        }

    }

}
</script>

<style>

</style>