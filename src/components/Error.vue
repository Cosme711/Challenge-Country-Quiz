<template>
  <div class="pb-8 flex justify-center items-center flex-col text-yellow-500">
    <h1
      class="text-3xl sm:text-5xl mx-8 font-bold text-center flex flex-col sm:flex-row"
    >
      <span class="mb-3 sm:mt-0 sm:pr-4 text-5xl">Oops !</span> Error Occured
    </h1>
    <p
      class=" lg:w-full sm:w-3/4 w-11/12  mt-8 pt-4 border-t border-opacity-75 border-grey text-white font-bold text-2xl tracking-wide"
    >
      Possible reason :
    </p>
    <ul
      class="lg:w-full sm:w-3/4 w-11/12 mt-6 list-disc list-inside text-white"
    >
      <li>Your internet connection.</li>
      <li class="py-2"><a href="">Rest Countries</a> API could be down.</li>
      <li>Your browser is not updated</li>
    </ul>
    <div class="mt-6 lg:w-full sm:w-3/4 w-11/12 flex">
      <a class="flex p-2 rounded cursor-pointer" @click="reload"
        ><span class="material-icons">refresh</span></a
      >
    </div>
  </div>
</template>

<script>
import { useStore } from "vuex";

export default {
  name: "Error",
  setup() {
    const store = useStore();

    function reload() {
      store.commit("CHANGE_ERROR", false);
      window.location.reload();
    }

    return { reload };
  }
};
</script>
