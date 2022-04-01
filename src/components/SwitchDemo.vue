<script lang="ts">
import { defineComponent, ref } from 'vue'
import Switch from '@/lib/Switch.vue'

export default defineComponent({
  name: 'SwitchDemo',
  components: {
    Switch
  },
  setup() {
    const availableRef = ref(false)

    return {
      availableRef
    }
  }
})
</script>

<template>
  <div>
    <Switch v-model:value="availableRef" />   
    <p>{{availableRef}}</p> 
  </div>
</template>
