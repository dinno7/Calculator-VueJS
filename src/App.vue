<template>

<Calculator class="calcultor"/>

</template>

<script>
import Calculator from './components/Calculator.vue';
export default {
  name: 'App',

  components:{
    Calculator,
  }
}
</script>

<style>
  body {
    background-image: url(./assets/backgroundPIC.png);
    background-repeat: no-repeat;
    background-position: center;
    background-attachment: fixed;
    background-size: cover;
    }
  .calcultor{
    animation: calcAnimation 1.5s;
    position: absolute;
    top:7%;
    left: 50%;
    transform: translateX(-50%);
    filter: drop-shadow(2px 3px 10px #000000af);
    }
  @keyframes calcAnimation {
    0%{
      opacity: 0;
      top: 0;
    }
    100%{
      opacity:1;
      top: 7%;
    }
} 
</style>
