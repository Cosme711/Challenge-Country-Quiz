<template>
  <main>
  </main>
</template>

<script>
import axios from 'axios';
import { onMounted, reactive} from "vue";

export default {
  name: 'App',
  setup() {

    const state = reactive({
      allQuestions: ''
    })

    function getData() {
      axios.get("https://restcountries.eu/rest/v2/all?fields=name;capital;flag")
      .then((response) => {
        state.allFlag = response.data
        console.log(state.allFlag)
      })
      .catch((error) => {
        console.log(error)
      })

    }

    onMounted(getData)
      return {
        getData
      }
    }
}

</script>

<style>

</style>
