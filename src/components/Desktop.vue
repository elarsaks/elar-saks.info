<template>
  <div :class="[ open ? 'desktop-wrapper' : 'desktop-wrapper-hidden' ]">
    <h1 class="section-header">
      {{sectionContent}}
      <img src="./../assets/down.png" />
    </h1>
    <component :is="sectionContent"></component>
  </div>
</template>

<script>
import About from './About.vue'
import Education from './Education.vue'
import Experience from './Experience.vue'
import Projects from './Projects.vue'
import Volunteering from './Volunteering.vue'
import Contact from './Contact.vue'

export default{
  props: ['open', 'sectionContent',],
    components: {
      Education,
      Experience,
      Projects,
      About,
      Volunteering,
      Contact
    },
}
</script>

<style scoped>
.desktop-wrapper {
  position: absolute;
  left: 17.5vw;
  top: 15vh;
  background-color: whitesmoke;
  height: 70vh;
  width: 65vw;
  z-index: 97;
  border-radius: 15px;
  overflow-y: scroll;
  -webkit-transition: all 1.9s;
  transition: all 1.9s;
}

.desktop-wrapper-hidden {
  position: absolute;
  left: 117.5vw;
  top: 15vh;
  background-color:rgba(245, 245, 245, 0);
  height: 70vh;
  width: 65vw;
  z-index: 97;
  border-radius: 15px;
  overflow-y: scroll;
  -webkit-transition: all 1.9s;
  transition: all 1.9s;
}

h1 {
  margin-left: 2vw;
  font-size: 4vh;
  width: 95%;
  float: left;
  margin-bottom: 2vh;
}

img {
  height: 4vh;
  float: right;
}

</style>