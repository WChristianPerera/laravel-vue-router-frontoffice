<script>
import axios from "axios";
import { store } from "../store";

export default {
  data() {
    return {
      store,
      arrCocktails: [],
    };
  },
  created() {
    axios.get(this.store.baseUrl + "api/cocktails/random").then((response) => {
      this.arrCocktails = response.data.results;
    });
  },
};
</script>

<template>

  <div class="container-fluid text-center">
        <div class="mask bg-dark m-3">
            <div class="d-flex justify-content-center align-items-center">
                    <div class="text-white m-2">
                    <h1 class="mb-3">The Cocktail Bar</h1>
                    <button class="button type1">
                        <router-link :to="{ name: 'cocktails.index' }" class="nav-link text-dark">COCKTAILS</router-link> </button>
                    </div>
            </div>
        </div>
  </div>

</template>