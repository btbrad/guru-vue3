<template>
  <div>
    默认：
    <guru-button @click="onClick">button</guru-button>
    <guru-button disabled>button</guru-button>
    <br />
    尺寸size:
    <guru-button @click="onClick" size="small" type="primary">small button</guru-button>
    <guru-button @click="onClick" size="large">large button</guru-button>
    <br />
    类型type：
    <guru-button @click="onClick" type="danger">danger</guru-button>
    <guru-button @click="onClick" type="link">button</guru-button>
    <guru-button @click="onClick" type="link" disabled>button</guru-button>
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
