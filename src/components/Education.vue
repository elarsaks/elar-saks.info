<template>
  <div class="content education">
    <h3>Haaga-Helia </h3>
    <h4>Bachelor’s in Business Information Technology</h4>
    <h4>08/2015 – 01/2019</h4>
    <p> Studying Business Information Technology, with a focus on software development. </p>
    <h4 class="cursor" @click="haagaShow = !haagaShow, hangShow=false" > Relevant Courses: </h4>


    <transition name="slide">
      <ul class="child" v-if="haagaShow">
        <li v-for="item in haaga" :key="item" >{{item}}</li>
      </ul>
    </transition>
    <br />

    <h3>Hang Seng Management College</h3>
    <h4> Exchange student</h4>
    <h4> 08/2015 – 01/2019 </h4>
    <p> Studied 1 semester in Hong Kong as part of Haaga Helia exchange student program. </p>
    <h4 class="cursor" @click="hangShow = !hangShow, haagaShow= false" >Relevant Courses:</h4>

    <transition name="slide">
      <ul class="child" v-if="hangShow">
        <li v-for="item in hang" :key="item" >{{item}}</li>
      </ul>
    </transition>
    <br />

    <h3>Helsinki Business College</h3>
    <h4>Associate Degree in Business Administration, Sales and Marketing</h4>
    <h4>08/2015 – 01/2019</h4>
    <p>
      Was awarded with European Business Baccalaureate Diploma during graduation, for
      outstanding performance.
    </p>
  </div>
</template>

<script>
export default{
  data(){
    return{
      haagaShow: false,
      hangShow: false,
      haaga:[ 'Multidisciplinary Software Project (React, Node JS, PostgreSQL)', 'Software Development Methods',
      'Data Management and Databases (SQL and Database design)', 'Mobile Programming (PhoneGap)', 'Server Programming (Java Spring)',
      'Front End Development (Html, CSS, JavaScript)', 'Programming (Java)', 'Software Project (Angular JS, Bootstrap)', 'Python programming'],
      hang: ['System Analysis and Design', 'SQL Lite and Database Design', 'Data Analytics (SAS)', 'Digital Marketing']
    }
  }
}
</script>


<style>

.education h3 {
  padding: 0;
  margin: 0;
}

.education  h4 {
  padding: 0;
  margin: 0;
}

.education li {
  padding: 0;
  margin: 0;
}

.education p{
  padding: 0;
  margin: 0.5vh;
  margin-left: 0;
}

.cursor {
   cursor: pointer;
   color: #1a3663;
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
