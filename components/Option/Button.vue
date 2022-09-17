<script setup lang="ts">
defineProps({
  isActive: {
    type: Boolean,
    required: false,
    default: false,
  },
});
</script>

<template>
  <button class="option"
          :class="{ 'option-active': isActive }">
    <slot />
  </button>
</template>

<style scoped>
.option {
  background: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}

.option:first-child {
  border-radius: 1rem 0 0 1rem;
}

.option:last-child{
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>
