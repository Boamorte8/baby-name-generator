<script setup lang="ts">
const props = defineProps({
  name: {
    type: String,
    required: true,
  },
});

const emit = defineEmits(['delete']);

const onDelete = () => emit('delete', props.name);
</script>

<template>
  <div class="card">
    <p>{{ name }}</p>
    <button class="close" @click="onDelete">X</button>
  </div>
</template>

<style scoped>
.card {
  background-color: rgb(27, 60, 138);
  width: 28%;
  color: white;
  border-radius: 1rem;
  padding: 1rem;
  display: flex;
  justify-content: center;
  position: relative;
}

.close {
  position: absolute;
  top: .5rem;
  right: .5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 1rem;
  width: 1rem;
  border-radius: 50%;
  border: none;
  background-color: transparent;
  color: rgba(255, 255, 255, 0.178);
  cursor: pointer;
}
</style>