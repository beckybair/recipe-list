<template>
  <div class="m-4">
    <h1>
      <i class="fas fa-utensils"></i>
      Recipe List
    </h1>
    <h2>
      Choose which a recipe to view:
    </h2>
    <div class="text-start">
      <recipe-list
        :recipes="recipes"
        @show-details="showDetails"
      ></recipe-list>
    </div>
    <div v-if="showRecipe" class="my-4">
      <recipe-details :recipe="recipes[activeRecipeIndex]"></recipe-details>
    </div>
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
