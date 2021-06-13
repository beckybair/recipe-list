<template>
  <div>
    <div class="d-lg-flex">
      <!-- Image -->
      <div
        id="images"
        class="col-lg-6 me-lg-3"
      >
        <!-- TODO: style -->
        <img
          :src="recipe.images.full"
          :alt="recipe.title"
          class="img-fluid d-none d-lg-block rounded mx-auto"
        >
        <img
          :src="recipe.images.medium"
          :alt="recipe.title"
          class="img-fluid d-none d-sm-block d-lg-none rounded mx-auto"
        >
        <img
          :src="recipe.images.small"
          :alt="recipe.title"
          class="img-fluid d-block d-sm-none rounded mx-auto"
        >
      </div>
      <!-- Title, Desctription, etc -->
      <div class="col-lg-6 mt-3">
        <p class="h3">{{ recipe.title }}</p>
        <p class="fs-6 mb-0 small">
          <em class="fw-bold">Posted on:</em> {{ recipe.postDate }}
        </p>
        <p
          v-if="recipe.editDate"
          class="fs-6 small"
        >
          <em class="fw-bold">Edited on:</em> {{ recipe.editDate }}
        </p>
        <p class="py-4">{{ recipe.description }}</p>
        <p class="fs-6 mb-0">
          <em class="fw-bold">Servings:</em> {{ recipe.servings }}
        </p>
        <p>
          <em class="fw-bold">Prep Time:</em> {{ recipe.prepTime }}m
          <i class="fas fa-minus" aria-hidden="true"></i>
          <em class="fw-bold"> Cook Time:</em> {{ recipe.cookTime }}m
        </p>
      </div>
    </div>

    <div class="d-lg-flex">
      <!-- Ingredients -->
      <div class="bt col-lg-4 mt-4 pt-3 me-lg-3">
        <p class="h4">Ingredients</p>
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
        class="bt b-lg-s col-lg-8 mt-4 pt-3 ps-lg-3"
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
@media (max-width: 991.98px) {
  .bt {
    border-top: 1px solid #dee2e6;
  }
}
@media (min-width: 992px) {
  .b-lg-s {
    border-left: 1px solid #dee2e6;
  }
}
</style>
