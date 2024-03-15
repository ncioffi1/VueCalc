<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

const counter = reactive({ 
  count: 0 
})

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
          <p class="calcText">{{ counter.count }}</p>
        </div>
        <div class="calcRow">
          <p class="buttonNum2">Clear</p>
          <p class="buttonEmpty"></p>
          <p class="buttonOp">÷</p>
        </div>
        <div class="calcRow">
          <p class="buttonNum">7</p>
          <p class="buttonNum">8</p>
          <p class="buttonNum">9</p>
          <p class="buttonOp">x</p>
        </div>
        <div class="calcRow">
          <p class="buttonNum">4</p>
          <p class="buttonNum">5</p>
          <p class="buttonNum">6</p>
          <p class="buttonOp">-</p>
        </div>
        <div class="calcRow">
          <p class="buttonNum">1</p>
          <p class="buttonNum">2</p>
          <p class="buttonNum">3</p>
          <p class="buttonOp">+</p>
        </div>
        <div class="calcRow">
          <p class="buttonNum2">0</p>
          <p class="buttonNum">.</p>
          <p class="buttonOp">=</p>
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
  border: 2px solid red;
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
  border: 1px solid blue;
  /* width: 400px;
  height: 100px; */
  width: 200px;
  height: 50px;
}
.calcRow {
  display: flex;
  flex-direction: row;
  align-items: center;
  border: 1px solid blue;
  width: 200px;
  height: 50px;
}
.buttonOp {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  /* text-align: center; */
  background-color: orange;
  border: 4px solid rgb(234, 106, 55);
  width: 50px;
  height: 50px;
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
  border: 4px solid rgb(197, 197, 197);
  width: 50px;
  height: 50px;
}

.buttonNum2 {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  background-color: gray;
  border: 4px solid rgb(197, 197, 197);
  width: 100px;
  height: 50px;
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
    top: 0;
    left: 50%;
    -webkit-transform: translate(-50%, 0);
    transform: translate(-50%, 0);
  border: 2px solid red;
}
.bar1B {
  display: flex;
  flex-direction: row;
  align-items: center;

  position: fixed;
    bottom: 10px;
    left: 50%;
    -webkit-transform: translate(-50%, 0);
    transform: translate(-50%, 0);
  border: 2px solid red;
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
