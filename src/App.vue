<script setup>
import colorsList from './assets/colorsList.json'
import {ref} from 'vue'
const colorChoosen = ref("rgb(255, 205, 210)")
const pick = (selectColor) => {
    colorChoosen.value = selectColor
    selectColor.style.boxShadow = "10px 10px 10px 10px v-bind(color)"

    // console.log(colorChoosen)
}
const shadow = () => {
}
</script>

<template>
  <header>
<h1>Selectionner une couleur</h1>
  </header>

  <main>
    <section class="colorContenair">
      <div v-for = "(color,index) in colorsList" :key="color[0]">
        <div v-for = "selectColor in color"
          :key="selectColor"
          :style="{backgroundColor: selectColor}"
          @click="pick(selectColor)"
          :class ="{ selected : selectColor === colorChoosen}"
          >
        </div>
      </div>

      </section>
      <section >
        <p>{{colorChoosen}}</p>
          <div class="colorPicker">
          </div>
    </section>


  </main>
</template>

<style scoped>
main{
  display: flex;
  align-content: center;
  flex: 1;
  justify-content: space-around;
  margin-top: 100px;
}
.colorContenair {
  display: flex;
  align-items: start;
  width: 500px;
  height: 500px;
  gap: 5px;
  /* border: 1px solid black; */
}

div>div{
  width: 50px;
  height: 50px;
  border: 1px solid black;
  margin-bottom: 5px;
  border-radius: 7px;
  border: 1px solid v-bind(color);
  cursor: pointer;

}
.colorPicker{
  width: 200px;
  height: 200px;
  border-radius: 7px;
  background-color: v-bind(colorChoosen);
}

.selected{
  box-shadow:  0px 0px 10px black;
}
</style>
