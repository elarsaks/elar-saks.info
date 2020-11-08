<template>
  <div class="content" v-bind:class="{ about: about }">

    <h3 v-if="exp.facility"> {{ exp.facility }} </h3>
    <h4 v-if="exp.position"> {{ exp.position }} </h4>
    <h4 class="date" v-if="exp.date"> {{ exp.date }} </h4>
    <p v-for="paragraph in exp.paragraphs" v-bind:key="paragraph" >{{paragraph}} </p>

    <!-- Education Specific. Consider making a separate compoent -->
    <ul v-if="exp.list && section != 'education'">
      <li v-for="item in exp.list" v-bind:key="item">{{item}}</li>
    </ul>
    <div class="courses" v-if="section == 'education' && exp.list">
      <h4 class="cursor" @click="showCourses = !showCourses" > Relevant Courses: </h4>
      <transition name="slide">
        <ul class="child" v-if="showCourses">
          <li v-for="item in exp.list" :key="item" >{{item}}</li>
        </ul>
      </transition>
    </div>



  </div>
</template>

<script>

  export default{
    props: ['exp', 'section'],
    data(){
      return{
        showCourses: false,
      }
    },
    computed: {
      about: function () {
        return this.section != 'about'
      }
  },
}
</script>

<style scoped>
.content {
  padding-bottom: 3vh;
  overflow-y: scroll;
}

h3 {
  padding: 0;
  margin: 0;
}

h4 {
  padding: 0;
  margin: 0;
}

ul {
  padding-top: 1vh;
  margin: 0;
}

li {
  padding: 0;
  margin: 0;
}

p {
  padding: 0;
  margin-bottom: 1vh;
}

.about p{
  margin-top: 0;
}

.courses  h4 {
  padding: 0;
  margin: 0;
}

.courses li {
  padding: 0;
  margin: 0;
}

.cursor {
   cursor: pointer;
   color: #1a3663;
}

.date {
  padding-bottom: 1vh;
}

.child {
  padding: 1vh;
  padding-left: 2vh;
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
   max-height: 100px;
   overflow: hidden;
}

@media (min-width:1023px){
  .content {
    padding-bottom: 3vh;
    overflow-y: hidden;
  } 
  h3 {
    font-size: 3vh;
    padding-top: 3vh;
  }

  h4 {
    font-size: 3vh;
    font-weight: 400;
  }

  li {
    font-size: 2.8vh;
  }

  p {
    font-size: 2.8vh;
  }

}
</style>
