<script setup lang="ts">
import { Gender, Length, names, OptionsState, Popularity } from './models/optionsState';

const options = reactive<OptionsState>({
  gender: Gender.GIRL,
  popularity: Popularity.UNIQUE,
  length: Length.SHORT,
});
const selectedNames = ref<string[]>([]);
const optionsArray = [
  {
    title: '1) Choose a gender',
    options: [Gender.BOY, Gender.UNISEX, Gender.GIRL],
    prop: 'gender',
  },
  {
    title: "2) Choose the name's popularity",
    options: [Popularity.TRENDY, Popularity.UNIQUE],
    prop: 'popularity',
  },
  {
    title: "3) Choose name's length",
    options: [Length.LONG, Length.ALL, Length.SHORT],
    prop: 'length',
  }
];

const onSelectOption = (value: string, prop: string) => {
  options[prop] = value;
}

const findNames = () => {
  selectedNames.value = names
    .filter((name) => name.gender === options.gender && name.popularity === options.popularity)
    .filter((name) => {
      if (options.length === Length.ALL) return true;
      else return name.length === options.length;
    })
    .map(name => name.name);
}

const onDelete = (name: String) => {
  selectedNames.value = selectedNames.value.filter(selectedName => selectedName !== name)
}
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>

    <p>Choose your options and click the "Find Names" buttom below</p>

    <div class="options-container">
      <OptionContainer v-for="option in optionsArray"
                        :title="option.title"
                        :options="option.options"
                        :selectedOption="options[option.prop]"
                        :key="option.prop"
                        @choose="onSelectOption($event, option.prop)"></OptionContainer>

      <button class="primary" @click="findNames">Find Names</button>
    </div>

    <CardContainer :names="selectedNames" @delete="onDelete"></CardContainer>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 3rem;
}

.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: .75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}
</style>
