<script setup lang="ts">
import { PropType } from 'vue';

defineProps({
  names: {
    type: Array as PropType<String[]>,
    required: false,
    default: [],
  },
});

const emit = defineEmits(['delete']);

const onDelete = (name: String) => emit('delete', name);
</script>

<template>
  <div class="cards">
    <CardName v-for="name in names" :key="name" :name="name" @delete="onDelete"></CardName>
  </div>
</template>

<style scoped>
.cards {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
  gap: .75rem;
}
</style>