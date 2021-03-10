<template>
  <div>
    <LikeHeader>
      <h3>はじめまして</h3>
    </LikeHeader>
    <LikeNumber :total-number="number" @my-click="incrementNumber"></LikeNumber>
    <button @click="currentComponent = 'Home'">Home</button>
    <button @click="currentCompontnt = 'About'">About</button>
    <keep-alive>
      <component :is="'currentComponent'"></component>
    </keep-alive>
    <About v-if="currentComponent === 'About'"></About>
    <Home v-if="currentComponent === 'Home'"></Home>
  </div>
</template>

<script>
import LikeHeader from "./components/LikeHeader.vue";
import About from "./components/About.vue";
import Home from "./components/Home.vue";

export default {
  data(){
    return {
      number : 10,
      currentComponent: "Home"
    }
  },
  components: {
    LikeHeader,
    About,
    Home
  },
  methods: {
    incrementNumber(value){
      return value + 1
    }
  }
}
</script>

<style scoped>
    div{
    border: 1px solid blue;
  }
  /* h1 {
    color: red;
  } */
</style>