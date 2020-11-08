<template>
  <div class="mobile">
    <div v-if="section != 'projects' && section != 'contact'">
      <ExpElement 
        v-for="exp in content" v-bind:key="exp.facility" 
        :exp="exp"
        :section="section"
      />
  </div>
  <div v-if="section == 'projects'" >
    <Project
      v-for="project in content" v-bind:key="project.name" 
      :project="project"
      :projectOpen="projectOpen"
      @showProject="openProject"
    />
  </div>
    <Contact
      v-if="section == 'contact'"
    />
  </div>
</template>

<script>
import Contact from './Contact.vue'
import ExpElement from './ExpElement.vue'
import Project from './Project.vue'

export default{
  props: ['content', 'section'],
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
        console.log(project, this.projectOpen)
        this.projectOpen = this.projectOpen == project ? false : project
      }
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
