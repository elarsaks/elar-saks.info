<template>
  <div class="section" >
    <h1 class="section-header" @click="select(header)">
      {{header}}
      <img src="./../assets/down.png" />
    </h1>
    <transition name="" >
      <div v-if="sectionContent == header">
        <component :is="sectionContent"></component>
      </div>
    </transition>
  </div>
</template>

<script>
import About from './About.vue'
import Education from './Education.vue'
import Experience from './Experience.vue'
import Projects from './Projects.vue'
import Volunteering from './Volunteering.vue'
import Contact from './Contact.vue'

export default {
  props: ['header', 'sectionContent', 'select'],
  components: {
    Education,
    Experience,
    Projects,
    About,
    Volunteering,
    Contact
  }
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


@media (min-width:600px){

}

</style>
