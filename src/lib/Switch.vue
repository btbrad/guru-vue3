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
  <button :class="['switch', {'open': value}]" @click="toggleStatus">
    <span></span>
  </button>
</template>

<style lang="scss" scoped>
  button {
    width: $switch-with-base;
    height: $switch-height-base;
    border: 1px solid #ccc;
    border-radius: $switch-border-radius;
    position: relative;
    cursor: pointer;
  }
  button > span {
    width: $switch-inner-width;
    height: $switch-inner-width;
    background: #fff;
    position: absolute;
    top: 1px;
    left: 2px;
    border-radius: 50%;
    transition: left .25s;
  }
  button.open {
    background: $primary;
  }
  button.open > span {
    left: calc(#{$switch-with-base} - #{$switch-inner-width} - 4px);
  }
</style>
