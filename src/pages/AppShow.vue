<script>
import axios from "axios";
import { store } from "../store";
import page404 from "./page404.vue";

export default {

  data() {
    return {
      cocktail: null,
      store,
    };
  },
  created() {
    axios
      .get(this.store.baseUrl + "api/cocktails/" + this.$route.params.cocktail)
      .then((response) => {
        if (response.data.success) {
          this.cocktail = response.data.results;
        }
      });
  },
};
</script>

<template v-if="cocktail">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <div id="container">

      <div class="product-details">
        <h1 class="text-center">{{ cocktail.strDrink }} <span>|</span> {{ cocktail.strAlcoholic }}</h1>
        <p class="information text-center px-5 mt-4">{{ cocktail.strInstructionsIT }}</p>
      </div>

      <div class="product-image">
        <img :src="cocktail.strDrinkThumb" :alt="cocktail.strDrink" />
      </div>

    </div>



  </template>