<template>
  <div>
    <p class="mb-0">
      {{ ingredient.amount }} {{ ingredient.measurement }} {{ ingredient.name }}
    </p>
    <p
      v-if="specialDisplayed"
      class="ms-3 mb-0 small text-danger"
    >
      {{ specialDisplayed }}
    </p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'RecipeIngredient',
  props: {
    ingredient: {
      type: Object,
      required: true,
    },
  },
  data: () => ({
    specials: [],
  }),
  async created() {
    try {
      const res = await axios.get('http://localhost:3001/specials');

      this.specials = res.data;
    } catch (e) {
      console.error(e);
    }
  },
  computed: {
    specialDisplayed() {
      let text = '';
      this.specials.forEach((special) => {
        if (special.ingredientId === this.ingredient.uuid) {
          text = `* ${special.title} - ${special.type} - ${special.text}`;
        }
      });
      return text;
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
