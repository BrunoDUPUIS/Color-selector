<script setup>
import colorsList from './assets/colorsList'
import { ref } from 'vue'
const selectedColor = ref('rgb(245, 245, 245)')
const selectColor = color => {
  selectedColor.value = color
}
</script>

<template>
  <main>
    <h1>Sélectionnez une couleur</h1>

    <div>
      <section>
        <div v-for="subColorsList in colorsList" :key="subColorsList[0]">
          <div
            v-for="color in subColorsList"
            :key="color"
            :style="{ backgroundColor: color }"
            @click="selectColor(color)"
            :class="{ selected: color === selectedColor }"
          ></div>
        </div>
      </section>
      <section>
        <p>{{ selectedColor }}</p>
        <div class="selectedColor"></div>
      </section>
    </div>
  </main>
</template>

<style scoped>
p {
  text-align: center;
  margin-bottom: 10px;
}
main {
  display: flex;
  flex-direction: column;
  /* background-color: pink; */
  height: 100vh;
}
div > div {
  /* border: 1px solid red; */
  width: 30px;
  height: 30px;
  border-radius: 3px;
}
section > div {
  display: flex;
  gap: 10px;
  margin-bottom: 10px;
}
h1 {
  font-weight: bold;
  text-align: center;
  font-size: 40px;
  margin-top: 30px;
}
.selectedColor {
  /* border: 1px solid red; */
  width: 200px;
  height: 200px;
  background-color: v-bind(selectedColor);
}
main > div {
  /* border: 3px solid blue; */
  display: flex;
  flex: 1;
  justify-content: center;
  align-items: center;
  gap: 50px;
}
.selected {
  box-shadow: 0px 0px 10px black;
}
</style>
