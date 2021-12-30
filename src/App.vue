<template>
  <div id="app">
    <router-view />
    <hr />
  </div>
</template>

<script lang="js">
import store from '@/store/index2'
   export default {
     data(){
       return {
         store: store
       }
     }
   } 
</script>


<style lang="scss">
@import "~@/assets/styles/reset.scss";
@import "~@/assets/styles/helper.scss";

body {
  font-family: $font-hei;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  line-height: 1.5;
  font-size: 16px;
  color: #333;
  background-color: #f5f5f5;
}

</style>
