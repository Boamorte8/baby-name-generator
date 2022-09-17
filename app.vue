<script setup lang="ts">
  import { Gender, Length, OptionsState, Popularity } from './models/optionsState';
  import OptionButton from './components/OptionButton.vue';

  const options = reactive<OptionsState>({
    gender: Gender.GIRL,
    popularity: Popularity.UNIQUE,
    length: Length.SHORT,
  });

  const names = ref<string[]>([]);

  const onClick = (prop: string, value: string) => {
    options[prop] = value;
  }
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>

    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <OptionButton :isActive="options.gender === Gender.BOY" @click="onClick('gender', Gender.BOY)">
            Boy
          </OptionButton>
          <OptionButton :isActive="options.gender === Gender.UNISEX" @click="onClick('gender', Gender.UNISEX)">
            Unisex
          </OptionButton>
          <OptionButton :isActive="options.gender === Gender.GIRL"  @click="onClick('gender', Gender.GIRL)">
            Girl
          </OptionButton>
        </div>
      </div>

      <div class="option-container">
        <h4>2) Choose the name's popularity</h4>
        <div class="option-buttons">
          <OptionButton :isActive="options.popularity === Popularity.TRENDY"
                        @click="onClick('popularity', Popularity.TRENDY)">
            Trendy
          </OptionButton>
          <OptionButton :isActive="options.popularity === Popularity.UNIQUE"
                        @click="onClick('popularity', Popularity.UNIQUE)">
            Unique
          </OptionButton>
        </div>
      </div>

      <div class="option-container">
        <h4>3) Choose name's length</h4>
        <div class="option-buttons">
          <OptionButton :isActive="options.length === Length.LONG" @click="onClick('length', Length.LONG)">
            Long
          </OptionButton>
          <OptionButton :isActive="options.length === Length.ALL" @click="onClick('length', Length.ALL)">
            All
          </OptionButton>
          <OptionButton :isActive="options.length === Length.SHORT" @click="onClick('length', Length.SHORT)">
            Short
          </OptionButton>
        </div>
      </div>

      <button class="primary">Find Names</button>
    </div>
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

.option-container {
  margin-bottom: 2rem;
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
