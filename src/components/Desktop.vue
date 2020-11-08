<template>
  <div :class="[ open ? 'desktop-wrapper' : 'desktop-wrapper-hidden' ]">
    <h1 class="section-header">
      {{content.header}}
      <img src="./../assets/down.png" />
    </h1>

    <div v-if="content.content && content.header != 'Contact' && content.header != 'Projects'">
      <ExpElement 
        v-for="exp in content.content" v-bind:key="exp.facility" 
        :exp="exp"
        :section="section"
      />
    </div>

    <div v-if="content.header == 'Projects'" >
      <Project
        v-for="project in content.content" v-bind:key="project.name" 
        :project="project"
        :projectOpen="projectOpen"
        @showProject="openProject"
      />
    </div>

    <Contact v-if="content.header == 'Contact'"/>
  </div>
</template>

<script>
import Contact from './Contact.vue'
import ExpElement from './ExpElement.vue'
import Project from './Project.vue'

export default{
  props: ['content', 'open',],
    components: {
      Contact,
      ExpElement,
      Project,
    },
    data(){
      return{
        projectOpen: false,
      }
    },
    methods:{
      openProject(project){
        this.projectOpen = this.projectOpen == project ? false : project
      }
    },
    computed: {
      section: function () {
        return this.content.header.toLowerCase()
      }
    },
    created(){
      console.log(this.content)
    }
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

.section-header {
  padding-top: 1vh;
  border-bottom: 1.5px solid;
  text-transform: uppercase;
  margin-top: 0;
  margin-bottom: 1vh;
  width: 98%;
}

h1 {
  margin-left: 2vh;
  font-size: 4vh;
  width: 95%;
  float: left;
  margin-bottom: 2vh;
}

img {
  height: 4vh;
  float: right;
}

@media (min-width:1023px){


}

</style>