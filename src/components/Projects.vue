<template>
  <div class="content projects">

    <div id="murupuru-div" @click="link(murupuru)">
      <h2 >MURUPURU </h2>
      <div class="project-box">
        <vue-friendly-iframe :src="murupuru" id="murupuru-page" />
      </div>
    </div>

    <div id="lauttasaarenSiivous-div" @click="link(lauttasaarenSiivous)">
      <br /><br />
      <h2>LAUTTASAARENSIIVOUS </h2>
      <div class="project-box" >
        <vue-friendly-iframe :src="lauttasaarenSiivous" id="lauttasaarenSiivous-page"/>
      </div>
    </div>
  </div>
</template>

<script>
import VueFriendlyIframe from 'vue-friendly-iframe';

  export default{
    components:{
      VueFriendlyIframe,
    },
    data(){
      return{
        murupuru: "http://www.murupuru.com",
        lauttasaarenSiivous: "http://www.lauttasaarensiivous.fi",
      }
    },
    methods: {
      link(link){
        window.open( link )
      }
    }
  }
</script>


<style>

.projects {
  text-align: center;
}

.project-header {
  padding: 0.5vh;
  width: 88vw;
}

.projects h2 {
  padding-top: 1vh;
}

.project-box {
  margin-left: 0;
  width: 90vw;
  height: 70vw;
  overflow: hidden;
  border-top: 1px solid;
  border-bottom: 1px solid;
}

.project-box p{
  text-align: center;
}

.vue-friendly-iframe {
  overflow: hidden;
}

#murupuru-page{
  margin-left: -5vw;
  margin-top: -30vh;
}

#lauttasaarenSiivous-page {
  margin-left: -5vw;
  margin-top: -25vh;
}

.vue-friendly-iframe iframe {
  width : 100vw;
  height: 100vh;
}



</style>
