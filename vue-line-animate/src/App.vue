<script setup>
import { ref } from 'vue';

const scroll = ref(false);
const total = ref(5);
const animationDuration = 10;

const img = (n) => {
  return {
    backgroundImage: `url(https://picsum.photos/1920/1200?random=${n})`,
    animationDuration: `${animationDuration}s`,
    animationDelay: `${((n - 1) * animationDuration) / 2}s`,
  };
};

window.addEventListener('scroll', function () {
  scroll.value = window.scrollY > 0;
});
</script>

<template>
  <div class="kv" :class="{ scroll }">
    <ul class="kvList">
      <li v-for="n in total" :style="img(n)"></li>
    </ul>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
body {
  height: 200vh;
}
.kv {
  position: relative;
  width: 100vw;
  height: 100vh;
  background-color: white;
}
.kvList {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.5s;
}
.kvList > li {
  position: absolute;
  width: 100%;
  height: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: 150% auto;
}
.kvList > li {
  animation-name: kvAnimate;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}
.scroll .kvList {
  width: 1200px;
  height: 300px;
}

@keyframes kvAnimate {
  0% {
    opacity: 0;
    background-size: 150% auto;
  }
  25% {
    opacity: 1;
  }
  50% {
    opacity: 1;
  }
  75% {
    opacity: 0;
  }
  to {
    opacity: 0;
    background-size: 120% auto;
  }
}
</style>
