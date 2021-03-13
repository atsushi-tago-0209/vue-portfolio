<template>
  <div>
    <p v-border:solid.round.shadow="{width: '5px',color: 'purple'}">Home</p>
    <h2>{{title | lowerCase | uppperCase }}</h2>
    <h2>{{subTitle | lowerCase}}</h2>
    <p>{{number}}</p>
    <button @click="number++">+1</button>
    <hr>
    <CountNumber></CountNumber>
  </div>
</template>

<script>
import CountNumber from "./CountNumber.vue";
import {tokyoNumber} from "@/tokyoNumber";

export default {
  mixins: [tokyoNumber],
  data(){
    return {
      tmpData: "hello",
    }
  },
  components:{
    CountNumber
  },
  directives: {
    border(el,binding) {
      el.style.borderWidth = binding.value.width;
      el.style.borderColor = binding.value.color;
      el.style.borderStyle = binding.arg;
      if(binding.modifiers.round){
        el.style.borderRadius = "0.5rem"
      }
      if(binding.modifiers.shadow){
        el.style.borderShadow = "0 2px 5px rgba(0,0,0,0.26)"
      }
    }
  }
}
</script>