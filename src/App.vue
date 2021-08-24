<template>
  <div id="app">
      <h1>Calculator</h1>
      <Calculator />
  </div>
</template>

<script>
import Calculator from "./main/Calculator.vue"

export default {
    components: { Calculator }
}
</script>

<style>
@font-face {
    font-family: "RobotoMono";
    src: url("./fonts/RobotoMono-Thin.ttf");
}

* {
    font-family: "RobotoMono", monospace;
}

body {
    margin: 0;
}

#app {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(to right, #0F2027, #203A43, #2C5364);
}
</style>