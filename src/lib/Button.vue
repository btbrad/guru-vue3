<template>
  <button class="guru-button" :class="classes">
    <slot/>
  </button>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'

export default defineComponent({
  name: 'Guru-Button',
  props: {
    size: {
      type: String,
      default: 'normal'
    },
    type: {
      type: String,
      default: 'primary'
    }
  },
  setup (props) {
    const { size, type } = props
    const classes = computed(() => {
      return {
        [`guru-${size}`]: size,
        [`guru-${type}`]: type
      }
    })
    return {
      classes
    }
  }
})
</script>

<style lang="scss" scoped>
.guru-button {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
  font-size: 16px;
  cursor: pointer;
  &:hover {
    background: $primary;
    color: #fff;
    border-color: #fff;
  }
  &.guru-small {
    font-size: 14px;
    padding: 3px;
  }
  &.guru-link {
    border: none;
    background: none;
    &:hover {
      color: $primary;
    }
  }
}
</style>