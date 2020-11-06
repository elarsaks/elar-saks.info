<template>
  <div 
    class="section" 
    :class="{ 'rounded-corners-up' : index === 'about', 'rounded-corners-down' : index === 'volunteering' }"
  >
    <h1 class="section-header" @click="select(item.header)">
      {{item.header}}
      <img src="./../assets/down.png" />
    </h1>
    <transition name="" >
        <MobileContent
          v-if="item.header == selected"
          :content="item.content"
        /> 
    </transition>
  </div>
</template>

<script>
import MobileContent from './MobileContent.vue'


export default {
  props: ["index", "item", 'select', 'selected'],
  components: {
    MobileContent,
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
