<template>
  <div class="main">
    <button @click="myAnimation ='slide'">Slide</button>
    <button @click="myAnimation ='fade'">Fade</button>
    <p>{{myAnimation}}</p>
    <button @click="show = !show">切り替え</button>
    <br><br>
    <transition
      @before-enter="beforeEnter"
      @enter="Enter"
      @after-enter="afterEnter"
      @enter-cancelled="enterCancelled"

      @before-enter="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
      @leave-cancelled="leaveCancelled"
    >
      <div class="circle" v-if="show"></div>
    </transition>
    <button @click="myComponent ='ComponentA'">ComponentA</button><br>
    <button @click="myComponent ='ComponentB'">ComponentB</button>
    <transition name="fade" mode="out-in">
      <component :is="myComponent"></component>
    </transition>
    <transition name="fade" mode="in-out">
      <p v-if="show" key="bye">さようなら</p>
      <p v-else key="hello">こんにちは</p>
    </transition>

    <transition
      name="fade"
      enter-active-class="animated bounce"
      leave-active-class="animated shake"
      appear
    >
    <p v-if="show">hello</p>
    </transition>
    <transition
      :name="myAnimation"
      appear
    >
    <p v-if="show">bye</p>
    </transition>

  </div>
</template>

<script>
import ComponentA from "./components/ComponentA.vue";
import ComponentB from "./components/ComponentB.vue";

export default {
  components:{
    ComponentA,
    ComponentB
  },
  data(){
    return {
      show :true,
      myAnimation: 'slide',
      myComponent: "ComponentA"
    }
  },
  methods:{
    beforeEnter(){},
    enter(){},
    afterEnter(){},
    enterCancelled(){},
    beforeLeave(){},
    leave(){},
    afterLeave(){},
    leaveCancelled(){},
  }
}
</script>

<style scoped>
.circle{
  width: 200px;
  height: 200px;
  margin: auto;
  border-radius: 100px;
  background-color: deeppink;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active {
  animation: slide-in 0.5s;
  transition: opacity 1s;
}
.fade-leave-active {
  animation: slide-in 1s reverse;
}
.slide-enter,
.slide-leave-to {
  opacity: 0;
}
.slide-enter-active {
  animation: slide-in 0.5s;
  transition: opacity 1s;
}
.slide-leave-active {
  animation: slide-in 1s reverse;
}

@keyframes slide-in {
  from {
    transform: translateX(100px);
  }
  to {
    transform: translateX(0);
  }
}
.main {
  width: 70%;
  margin: auto;
  padding-top: 5rem;
  text-align: center;
}
</style>