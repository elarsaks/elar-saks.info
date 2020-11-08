<template>
  <div class="project">
      <img 
        class="project-img" 
        :src="project.image"
        @click="$emit('show-project', project.name)" 
      />

      <transition name="slide">
        <div
          v-if="projectOpen == project.name"
          class="project-info"
        >
          <h3> {{ project.name }} </h3>
          <h4> {{ project.role }} </h4>
          <h4 class="time"> {{ project.time }} </h4>
          <h4 class="in-text">Technologies: </h4>
          <p> {{project.technologies}} </p>

          <h4 class="in-text">Description: </h4>
          <p v-for="p in project.description" v-bind:key="p" > {{ p }} </p>

          <h4 class="in-text">Links: </h4>
          <div v-for="link in project.links" v-bind:key="link.link">
            <p class="links">
              {{ link.text }}
              <br v-if="windowWith < 1024" >
              <a @click="openLink(link.link)">{{ link.link }}</a>
            </p>
          </div>
      </div>
      </transition>
  </div>
</template>

<script>
export default {
  props: ['project', 'projectOpen'],
  methods: {
    openLink(adress){
      window.open( adress )
    },
  }
}
</script>

<style scoped>
h3 {
  padding: 0;
  margin: 0;
  font-size: 4vh;
}

h4 {
  padding: 0;
  margin: 0;
  font-size: 3vh;
}

.in-text {
  padding: 0;
}

p {
  padding: 0;
  padding-bottom: 2vh;
  font-size: 3vh;
  margin: 0;
}

.project {
  text-align: center;
}

.project-info {
  text-align: center;
  border-radius: 2vh;
}

.project-img {
  width: 100%;
  height: 30vh;
  border-radius: 2vh;
  border: 1px solid black;
}

.time {
  padding-bottom: 1vh;
}

.links {
  padding: 0;
  margin: 0;
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
   overflow: hidden;
}

@media (min-width:1023px) {

  a {
    text-decoration: underline;
    color: blue;
  }

  .project {
    padding-bottom: 0;
    padding-top: 5vh;
  }

  .project-img {
    width: 40vw;
    height: 50vh;
    margin-left: auto;
    margin-right: auto;
  }

  .project-info {
    margin-top: 0;
    margin-left: auto;
    margin-right: auto;
    width: 40vw;
  }
}
</style>
