<template>
  <div class="mobile">
    <ExpElement 
      v-for="exp in content" v-bind:key="exp.facility" 
      :exp="exp"
      :section="section"
    />
  </div>
</template>

<script>
import ExpElement from './ExpElement.vue'

export default{
  props: ['content', 'section'],
    components: {
      ExpElement,
    },
}
</script>

<style>
</style>
