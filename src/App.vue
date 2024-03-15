<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

import {reactive} from 'vue'

const counter = reactive({ 
  count: 0, 
  count2: 0,
  activeOp: "",
  calculated: false,
  setActiveOp: false
})

function calculate() {
  // console.log("===");
  // console.log(counter.activeOp);

  if (counter.activeOp === "+") {
    add();
  } else if (counter.activeOp === "-") {
    subtract();
  } else if (counter.activeOp === "*") {
    multiply();
  } else if (counter.activeOp === "÷") {
    divide();
  }
  counter.calculated = true;
}
function increment(num) {
  if (counter.activeOp === "" || counter.calculated) {
    if (counter.count === 0 || counter.calculated) {
      counter.calculated = false;
      counter.count = num;
    } else {
      counter.count = counter.count * 10 + num;
    }
  } else {
    counter.setActiveOp = true;
    if (counter.count2 === 0) {
      counter.count2 = num;
    } else {
      counter.count2 = counter.count2 * 10 + num;
    }
  }
}

function add() {
  counter.count = counter.count + counter.count2;
  counter.count2 = 0;
  clearOp();
}
function subtract() {
  counter.count = counter.count - counter.count2;
  counter.count2 = 0;
  clearOp();
}
function multiply() {
  console.log('called multiply');
  console.log(counter.count);
  console.log(counter.count2);
  console.log(counter.count * counter.count2);
  counter.count = counter.count * counter.count2;
  counter.count2 = 0;
  clearOp();
}
function divide() {
  console.log('called divide');
  console.log(counter.count);
  console.log(counter.count2);
  console.log(counter.count / counter.count2);
  counter.count = counter.count / counter.count2;
  counter.count2 = 0;
  clearOp();
}
function clear() {
  clearOp();
  counter.count = 0;
  counter.count2 = 0;
  counter.calculated = false;
}
function setOp(operation) {
  counter.activeOp = operation;  // ex op = "-"
}
function clearOp() {
  counter.activeOp = "";
  counter.setActiveOp = false;
}
function getCount() {
  if (!counter.setActiveOp) {
    return counter.count;
  } else {
    return counter.count2;
  }

}

</script>

<template>
  <header>
   
    
    <!-- <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div> -->
  </header>

  <main>
    <div class="bar1">
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
      <p class="title">Vue Calc</p>
    </div>
    <div class="bar1B">
      <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->
      <p class="title">Made in Vue by Nick Cioffi</p>
    </div>
    <div class="bar2">
      <div class="calcHolder">
        <div class="calcRowB">
          <p class="calcText">{{ getCount() }}</p>
        </div>
        <div class="calcRow">
          <button @click="clear" class="buttonNum2">Clear</button>
          <p class="buttonEmpty"></p>
          <button v-if="counter.activeOp === '÷'" @click="setOp('÷')" class="buttonOp" id="opActive">÷</button>
          <button v-else @click="setOp('÷')" class="buttonOp" id="op">÷</button>
          
        </div>
        <div class="calcRow">
          <button @click="increment(7)" class="buttonNum">7</button>
          <button @click="increment(8)" class="buttonNum">8</button>
          <button @click="increment(9)" class="buttonNum">9</button>
          <button v-if="counter.activeOp === '*'" @click="setOp('*')" class="buttonOp" id="opActive">x</button>
          <button v-else @click="setOp('*')" class="buttonOp" id="op">x</button>
         
        </div>
        <div class="calcRow">
          <button @click="increment(4)" class="buttonNum">4</button>
          <button @click="increment(5)" class="buttonNum">5</button>
          <button @click="increment(6)" class="buttonNum">6</button>
          <button v-if="counter.activeOp === '-'" @click="setOp('-')" class="buttonOp" id="opActive">-</button>
          <button v-else @click="setOp('-')" class="buttonOp" id="op">-</button>
          
        </div>
        <div class="calcRow">
          <button @click="increment(1)" class="buttonNum">1</button>
          <button @click="increment(2)" class="buttonNum">2</button>
          <button @click="increment(3)" class="buttonNum">3</button>
          <button v-if="counter.activeOp === '+'" @click="setOp('+')" class="buttonOp" id="opActive">+</button>
          <button v-else @click="setOp('+')" class="buttonOp" id="op">+</button>
        </div>
        <div class="calcRow">
          <button class="buttonNum2">0</button>
          <p class="buttonEmpty"></p>
          <!-- <button class="buttonNum">.</button> -->
          <button @click="calculate" class="buttonOp" id="op">=</button>
        </div>
      </div>
    </div>
    <!-- <TheWelcome /> -->
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}
.calcHolder {
  /* border: 2px solid red; */
  width: 200px;
  height: 300px;
}
.calcText {
  font-size: 36px;
  margin-right: 12px;
}

.calcRowB {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: right;
  /* border: 1px solid blue; */
  /* width: 400px;
  height: 100px; */
  width: 200px;
  height: 50px;
}
.calcRow {
  display: flex;
  flex-direction: row;
  align-items: center;
  /* border: 1px solid blue; */
  width: 200px;
  height: 50px;
}
.buttonOp {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  color: black;
  border-radius: 10px;
  background-color: orange;
  /* border: 4px solid rgb(234, 106, 55); */
  width: 48px;
  margin: 1px;
  height: 48px;
}
#op{
  border: 4px solid rgb(234, 106, 55);
}
#opActive {
  border: 6px solid rgb(144, 86, 56);
  /* border: 6px solid rgb(234 - 20, 106 - 20, 55 - 20); */
}
.buttonEmpty {
  width: 50px;
  height: 50px;
}
.buttonNum {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  background-color: gray;
  border: 1px solid rgb(197, 197, 197);
  border-radius: 10px;
  width: 48px;
  margin: 1px;
  height: 48px;
}

.buttonNum2 {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  background-color: gray;
  border: 1px solid rgb(197, 197, 197);
  border-radius: 10px;
  width: 98px;
  margin: 1px;
  height: 48px;
}

.bar2 {
  position: fixed;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
}
.bar1 {
  display: flex;
  flex-direction: row;
  align-items: center;

  position: fixed;
    top: 10px;
    left: 50%;
    -webkit-transform: translate(-50%, 0);
    transform: translate(-50%, 0);
}
.bar1B {
  display: flex;
  flex-direction: row;
  align-items: center;

  position: fixed;
    bottom: 20px;
    left: 50%;
    -webkit-transform: translate(-50%, 0);
    transform: translate(-50%, 0);
}
.title {
  font-size: 36px;
}

.logo {
  display: block;
  /* margin: 0 auto 2rem; */
}

/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
