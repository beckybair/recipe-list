<template>
  <div>
    <p class="h4 text-lg-start">Directions</p>
    <div class="text-start pt-3">
      <p
        v-for="(direction, index) in directions"
        :key="index"
        class="mb-0"
      >
        {{ direction.instructions }}
        <em v-if="direction.optional">
          (this is optional)
        </em>
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
