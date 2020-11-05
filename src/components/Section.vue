<template>
  <div class="section" >
    <h1 class="section-header" @click="select(item.header)">
      {{item.header}}
      <img src="./../assets/down.png" />
    </h1>
    <transition name="" >
        <Mobile 
          v-if="item.header == selected"
          :content="item.content"
        /> 
    </transition>
  </div>
</template>

<script>
import Mobile from './Mobile.vue'


export default {
  props: ["item", 'select', 'selected'],
  components: {
    Mobile,
  },
}

</script>

<style>

.section {
  padding: 2vw;
  padding-right: 3vw;
  background-color: #fff;
  margin-top: 3vh;
}

.section-header {
  padding-top: 1vh;
  border-bottom: 1.5px solid;
  font-size: 5vw;
  text-transform: uppercase;
  margin-top: 0;
  margin-bottom: 1vh;
}

.section img {
  height: 0.9em;
  float: right;
}

.content {
  padding-left: 1vw;
  padding-right: 1vw;
  font-size: 4vw;
}

.content a{
  font-weight: 200;
}


</style>
