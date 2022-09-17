<script setup lang="ts">
import { PropType } from 'vue';

defineProps({
  title: {
    type: String,
    required: true,
  },
  selectedOption: {
    type: String,
    required: true,
  },
  options: {
    type: Array as PropType<String[]>,
    required: false,
    default: [],
  },
});

const emit = defineEmits(['choose']);

const onClick = (value: String) => {
  emit('choose', value);
}
</script>

<template>
  <div class="option-container">
    <h4>{{ title }}</h4>

    <div class="option-buttons">
      <OptionButton v-for="option in options"
                    :key="option"
                    :isActive="selectedOption === option"
                    @click="onClick(option)">
        {{ option }}
      </OptionButton>
    </div>
  </div>
</template>

<style scoped>
.option-container {
  margin-bottom: 2rem;
}
</style>
