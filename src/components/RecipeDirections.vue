<template>
  <div class="border-start mt-4 ps-md-3">
    <h3 class="text-md-start">Directions</h3>
    <div class="text-start pt-3">
      <p
        v-for="(direction, index) in directions"
        :key="index"
        class="mb-0"
      >
        {{ direction.instructions }}
        <span
         v-if="direction.optional"
         class="fst-italic"
        >
          (this is optional)
        </span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RecipeDirections',
  props: {
    directions: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
