<template>
  <div class="m-4">
    <header class="border-bottom mb-4">
      <h1>
        <i class="fas fa-utensils" aria-hidden="true"></i>
        Dinner Time
      </h1>
    </header>

    <main>
      <section>
        <p class="h2">
          Recipe List
        </p>
        <p class="mb-0 mt-3">
          Choose which recipe to view:
        </p>
        <div class="col-12 col-lg-4 mx-auto text-start">
          <recipe-list
            :recipes="recipes"
            @show-details="showDetails"
          ></recipe-list>
        </div>
      </section>

      <section>
        <div v-if="showRecipe" class="border-top mt-4 mb-4 pt-4">
          <p class="h2 mb-3">
            Recipe Details
          </p>
          <recipe-details :recipe="recipes[activeRecipeIndex]"></recipe-details>
        </div>
      </section>
    </main>
    <footer class="border-top mt-4">
      <p class="pt-4">©Copyright 2021 by Somebody. All rights reversed.</p>
    </footer>
  </div>
</template>

<script>
import axios from 'axios';
import RecipeDetails from './RecipeDetails.vue';
import RecipeList from './RecipeList.vue';

export default {
  components: { RecipeList, RecipeDetails },
  name: 'Home',
  data: () => ({
    recipes: [],
    activeRecipeIndex: null,
    showRecipe: false,
  }),
  async created() {
    try {
      const res = await axios.get('http://localhost:3001/recipes');

      this.recipes = res.data;
    } catch (e) {
      console.error(e);
    }
  },
  methods: {
    showDetails(activeRecipeIndex) {
      this.activeRecipeIndex = activeRecipeIndex;
      this.showRecipe = true;
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
