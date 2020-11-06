<template>
  <div class="mobile">
    <ExpElement 
      v-for="exp in content" v-bind:key="exp.facility" 
      :exp="exp"
    />
  </div>
</template>

<script>
import ExpElement from './ExpElement.vue'

export default{
  props: ['content',],
    components: {
      ExpElement,
    },
}
</script>

<style>
</style>
