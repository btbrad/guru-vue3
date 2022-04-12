<template>
  <div>
    默认：
    <guru-button @click="onClick">button</guru-button>
    <br />
    尺寸size:
    small: <guru-button @click="onClick" size="small">button</guru-button>
    <br />
    类型type：
    link: <guru-button @click="onClick" type="link">button</guru-button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import GuruButton from '@/lib/Button.vue'

export default defineComponent({
  name: 'Button-Demo',
  components: {
    GuruButton
  },
  setup () {
    const onClick = () => {
      alert('clicked!')
    }
    return {
      onClick
    }
  }
})
</script>

<style lang="scss" scoped>

</style>