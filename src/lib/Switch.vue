<script lang="ts">
import { defineComponent, ref } from 'vue'

 export default defineComponent({
   name: 'Switch',
   props: {
     value: Boolean
   },
   setup (props, context) {
     const toggleStatus = () => {
       context.emit('update:value', !props.value)             
     }

     return {
       toggleStatus
     }
   }
 })
</script>

<template>
  <button :class="{'open': value}" @click="toggleStatus">
    <span></span>
  </button>
</template>

<style lang="scss" scoped>
  $h: 22px;
  $h2: $h - 4px;
  button {
    width: $h * 2;
    height: 20px;
    border: 1px solid #ccc;
    border-radius: calc(#{$h}/2);
    position: relative;
    cursor: pointer;
  }
  button > span {
    width: $h2;
    height: $h2;
    background: #fff;
    position: absolute;
    top: 0;
    left: 0;
    border-radius: calc(#{$h2} / 2);
    transition: left .25s;
  }
  button.open {
    background: #0f0;
  }
  button.open > span {
    left: calc(#{$h} * 2 - #{$h2} - 2px);
  }
</style>