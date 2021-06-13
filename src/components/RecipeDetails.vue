<template>
  <div>
    <div class="d-flex">
      <!-- Image -->
      <div
       id="images"
       class="col-md-6 me-md-3"
       >
        <!-- TODO: style -->
        <img
          :src="recipe.images.full"
          alt=""
          class="img-fluid d-none d-lg-block rounded mx-auto"
          aria-labelledby="recipeTitle"
        >
        <img
          :src="recipe.images.medium"
          alt=""
          class="img-fluid d-none d-sm-block d-lg-none rounded mx-auto"
          aria-labelledby="recipeTitle"
        >
        <img
          :src="recipe.images.small"
          alt=""
          class="img-fluid d-block d-sm-none rounded mx-auto"
          aria-labelledby="recipeTitle"
        >
      </div>
      <!-- Title, Desctription, etc -->
      <div class="col-md-6 mt-3">
        <h2 id="recipeTitle">{{ recipe.title }}</h2>
        <p class="fs-6 mb-0">
          <span class="fw-bold fst-italic">Posted on:</span> {{ recipe.postDate }}
        </p>
        <p
          v-if="recipe.editDate"
          class="fs-6"
        >
          <span class="fw-bold fst-italic">Edited on:</span> {{ recipe.editDate }}
        </p>
        <p class="py-4">{{ recipe.description }}</p>
        <p class="fs-6 mb-0">
          <span class="fw-bold">Servings:</span> {{ recipe.servings }}
        </p>
        <p>
          <span class="fw-bold">Prep Time:</span> {{ recipe.prepTime }}m
          <i class="fas fa-minus"></i>
          <span class="fw-bold"> Cook Time:</span> {{ recipe.cookTime }}m
        </p>
      </div>
    </div>

    <div class="d-flex">
      <!-- Ingredients -->
      <div class="col-md-4 mt-4 me-md-3">
        <h3>Ingredients</h3>
        <div class="text-start pt-3">
          <recipe-ingredient
            v-for="(ingredient, index) in recipe.ingredients"
            :key="index"
            :ingredient="ingredient"
            class="mb-0"
          ></recipe-ingredient>
        </div>
      </div>

      <!-- Directions -->
      <recipe-directions
        v-if="recipe.directions"
        :directions="recipe.directions"
        class="col-md-8"
      ></recipe-directions>
    </div>
  </div>
</template>

<script>
import RecipeIngredient from './RecipeIngredient.vue';
import RecipeDirections from './RecipeDirections.vue';

export default {
  components: { RecipeIngredient, RecipeDirections },
  name: 'RecipeDetails',
  props: {
    recipe: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
