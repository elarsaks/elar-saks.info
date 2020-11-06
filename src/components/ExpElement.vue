<template>
  <div class="content">
    <h3 v-if="exp.facility"> {{ exp.facility }} </h3>
    <h4 v-if="exp.position"> {{ exp.position }} </h4>
    <h4 v-if="exp.date"> {{ exp.date }} </h4>
    <p v-for="paragraph in exp.paragraphs" v-bind:key="paragraph">{{paragraph}}</p>

    <ul v-if="exp.list && section == 'experience'">
      <li v-for="item in exp.list" v-bind:key="item">{{item}}</li>
    </ul>

  <div class="courses">
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
created(){
    console.log(this.exp)
    }
  }
</script>


<style scoped>
.content {
  padding-bottom: 5vh;
}

.content h3 {
  padding: 0;
  margin: 0;
}

.content h4 {
  padding: 0;
  margin: 0;
}

.content ul {
  padding-top: 1vh;
  margin: 0;
}

.content li {
  padding: 0;
  margin: 0;
}

.content p{
  padding: 0;
  margin-top: 0;
  margin-bottom: 2vh;
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

.slide-enter-active {
   transition: all .3s ease-in;
}

.slide-leave-active {
   transition: all .3s ease-in;
}

.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

@media (min-width:1023px){
  .content h3 {
    font-size: 3vh;
    padding-top: 3vh;
  }

  .content h4 {
    font-size: 3vh;
    font-weight: 400;
  }

  .content li {
    font-size: 3vh;
  }

  .content p {
    font-size: 3vh;
  }

}
</style>
