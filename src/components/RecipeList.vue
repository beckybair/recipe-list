<template>
  <div
    v-if="recipes"
    class="list-group"
  >
    <button
     v-for="(recipe, index) in recipes"
     :key="index"
     class="list-group-item list-group-item-action flex-fill"
     :class="{ 'active': index === activeRecipe }"
     type="button"
     :aria-current="index === activeRecipe"
     @click.prevent="showDetails(index)"
    >
      {{ recipe.title }}
    </button>
  </div>
  <div v-else>
    There are no recipes to list - please try again later.
  </div>
</template>

<script>
export default {
  name: 'RecipeList',
  props: {
    recipes: {
      type: Array,
      default: () => [],
    },
  },
  data: () => ({
    activeRecipe: null,
  }),
  methods: {
    showDetails(index) {
      this.activeRecipe = index;
      this.$emit('showDetails', this.activeRecipe);
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
