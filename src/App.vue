<template>
  <main>
    <p>{{ state.capitalAnswer.capital }} is the capital of</p>
    <ul>
      <li v-for="response in state.capitalResponse" :key="response.id">{{ response.name }}</li>
    </ul>
  </main>
</template>

<script>
import axios from 'axios';
import { onMounted, reactive} from "vue";

export default {
  name: 'App',
  setup() {

    const state = reactive({
      capitalAnswer: '',
      capitalResponse: []
    })

    const getData = async () => {
      const { data } = await axios.get(
        "https://restcountries.eu/rest/v2/all?fields=name;capital;flag"
      );

      const index = Math.floor(Math.random() * 250);
      state.capitalAnswer = data[index];
      console.log(state.capitalAnswer)
      
      let j = 0;
      while (j < 3) {
        const index = Math.floor(Math.random() * 250);
        let allResponse = data[index];
        
        state.capitalResponse.push(allResponse);
        allResponse = ''
        j++;
      }
      state.capitalResponse.push(state.capitalAnswer)
      console.log(state.capitalResponse)
    };

    onMounted(getData);
      return {
        getData,
        state
      }
  }
}

</script>

<style>

</style>
