<script setup>
import ReviewListItem from './ReviewListItem.vue'

defineProps({
  filteredReviews: {
    type: Array,
    required: true,
  },
})
</script>

<template>
  <ul class="review-tiles">
    <li v-if="filteredReviews.length === 0" class="reviews-tiles__item reviews-tiles__item--empty">
      <p>Нет отзывов по выбранному фильтру.</p>
    </li>
    <ReviewListItem
      v-for="(review, index) in filteredReviews"
      :key="review.id"
      v-bind:review="review"
      @remove-review="() => $emit('remove-review', index)"
      @toggle-like="() => $emit('toggle-like', review)"
    />
  </ul>
</template>

<style scoped>
.review-tiles {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  gap: 1rem;
  padding: 0;
}
</style>
