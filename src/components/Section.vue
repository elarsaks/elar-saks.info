<template>
  <div 
    class="section" 
    :class="{ 'rounded-corners-up' : index === 'about', 'rounded-corners-down' : index === 'contact' }"
  >
    <h1 class="section-header" @click="$emit('change-content', this.item.header)">
      {{item.header}}
      <img src="./../assets/down.png" />
    </h1>
    <transition name="slide" >
        <MobileContent
          v-if="item.header == section"
          :content="item.content"
          :section="index"
        /> 
    </transition>
  </div>
</template>

<script>
import MobileContent from './MobileContent.vue'


export default {
  props: ["index", "item", 'section'],
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

.slide-enter-active {
   -moz-transition-duration: 0.3s;
   -webkit-transition-duration: 0.3s;
   -o-transition-duration: 0.3s;
   transition-duration: 0.3s;
   -moz-transition-timing-function: ease-in;
   -webkit-transition-timing-function: ease-in;
   -o-transition-timing-function: ease-in;
   transition-timing-function: ease-in;
}

.slide-leave-active {
   -moz-transition-duration: 0.3s;
   -webkit-transition-duration: 0.3s;
   -o-transition-duration: 0.3s;
   transition-duration: 0.3s;
   -moz-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   -webkit-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   -o-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
}

.slide-enter-to, .slide-leave {
   max-height: 100px;
   overflow: hidden;
}

.slide-enter, .slide-leave-to {
   overflow: hidden;
   max-height: 0;
}

</style>
