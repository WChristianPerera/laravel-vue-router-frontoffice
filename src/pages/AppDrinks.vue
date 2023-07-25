<script>
import axios from "axios";
export default {
  data() {
    return {
      drinks: [],
      currentPage: 1,
      nPages: 0,
      loader: true,
    };
  },
  methods: {
    getDrinks() {
      (this.loader = true),
        axios
          .get("http://localhost:8000/api/drinks", {
            params: {
              page: this.currentPage,
            },
          })
          .then((response) => {
            this.drinks = response.data.results.data;
            this.nPages = response.data.results.last_page;
            this.loader = false;
          });
    },
    changePage(page) {
      this.currentPage = page;
    },

  },
  created() {
    this.getDrinks();
  },
  watch: {
    currentPage() {
      this.getDrinks();
    },
  },
};
</script>

<template>
    <main>

        <div class="container">
        
            <h1 class="text-center mt-3">I Nostri Cocktails</h1>
            
            <div v-if="!loader" class="row row-cols-3 g-5 my-5">
                <div v-for="drink in drinks" :key="drink.id" class="col z-3">
                <router-link
                    class="text-decoration-none"
                    :to="{ name: 'drinks.show', params: { id: drink.id } }"
                >
                    <div class="drink_card">
                    <img
                        class="h-100"
                        :src="drink.strDrinkThumb"
                        :alt="drink.strDrink"
                    />
                    <p class="fs-6">{{ drink.strDrink }}</p>
                    </div>
                </router-link>
                </div>
            </div>
            <div v-else>
                <div class="loader">
                <div class="loader_cube loader_cube--color"></div>
                <div class="loader_cube loader_cube--glowing"></div>
                </div>
            </div>
            
            <nav>
                <div class="pagination p6">
                    <ul>
                        <a
                        href="#"
                        v-for="page in nPages"
                        :key="page"
                        class="page-item"
                        :class="{ is_active: page == currentPage }"
                        @click="changePage(page)"
                        ><li></li
                        ></a>
                    </ul>
                </div>
            </nav>

        </div>
  </main>
</template>