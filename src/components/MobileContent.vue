<template>
  <div class="mobile">
    <ExpElement 
      v-for="exp in content" v-bind:key="exp.facility" 
      :exp="exp"
      :section="section"
    />
    <Contact
      v-if="section == 'contact'"
    />
  </div>
</template>

<script>
import ExpElement from './ExpElement.vue'
import Contact from './Contact.vue'

export default{
  props: ['content', 'section'],
    components: {
      ExpElement,
      Contact,
    },
}
</script>

<style>
#mobile{
  border-radius: 2vh;
  background-color: rgb(0,0,0,0.2);
  margin-left: auto;
  margin-right: auto;
  padding-bottom: 5vh;
  width: 95vw;
  padding-bottom: 0;
}
</style>
