<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <p>{{ ironman }}</p>
    <p>{{ hulk}}</p>

    <button @click="changeIronMan">Cambiar ironman</button>
    <button @click="changeHulk">Cambiar hulk</button>

    <h3>Ironman: {{ ironmanIsAlive}}</h3>
    <h3>Hulk: {{ hulkIsAlive }}</h3>

    <button @click="changeStatus">Cambiar Status</button>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'HomeView',
  setup(){

    const ironman = ref({name: 'Tony', age: 50})
    const hulk = reactive({name: 'Bruce', age: 50})

    const ironmanIsAlive = reactive(false)
    const hulkIsAlive = ref(true)

    const changeStatus = () => {
      hulkIsAlive.value = !hulkIsAlive.value
      ironmanIsAlive = !ironmanIsAlive
    }

    return{
      ironman,
      hulk,
      ironmanIsAlive,
      hulkIsAlive,

      changeStatus,

      changeIronMan: () => {
        ironman.value.name = 'Tony Stark'
        ironman.value.age = 45
      },

      changeHulk: () => {
        hulk.name = 'Bruce Banner'
        hulk.age = 45
      }
    }
  }
}
</script>
