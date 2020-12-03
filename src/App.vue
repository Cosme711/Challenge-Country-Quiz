<template>
  <main>
    <p>Capital of {{ state.countryAnswer.name }}?</p>
  </main>
</template>

<script>
import axios from 'axios';
import { onMounted, reactive} from "vue";

export default {
  name: 'App',
  setup() {

    const state = reactive({
      countryAnswer: '',
    })

    const getData = async () => {
      const selectedIndex = [];
      const { data } = await axios.get(
        "https://restcountries.eu/rest/v2/all?fields=name;capital;flag"
      );
      let i = 0;
      while (i < 5) {
        let j = 0;
        const eachQuestion = {
          list: [],
          answer: Math.floor(Math.random() * 4)
        };
        while (j < 4) {
          const index = Math.floor(Math.random() * 250);
          state.countryAnswer = data[index];

          selectedIndex.push(index);
          eachQuestion.list.push(state.countryAnswer);
          j++;
        }
        i++;
      }
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
