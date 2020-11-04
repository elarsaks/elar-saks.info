<template>
  <div class="content experience">

    <ExpElement v-for="exp in experiences" v-bind:key="exp.facility" :exp="exp" />

    <h3>Edita Publishing </h3>
    <h4>Software Developer Trainee</h4>
    <h4>01/2020 – 06/2020</h4>
    <ul>
      <li>Worked as a member of an agile development team, participated in daily-, sprint- and monthly meetings. </li> 
      <li>Built user interfaces and REST API-s, based on senior team members specifications.</li>
      <li>Technical tools used daily: JavaScript (Vue, Node), PostgreSQL, Docker, Linux, Github, Slack, Jira and etc..</li>
    </ul>

    <h3>MuruPuru OY</h3>
    <h4>Owner / Freelance Web Developer</h4>
    <h4>01/2017 – Present </h4>

    <ul>
      <li>Created a company and its online presence <a @click="link(murupuru)" >www.murupuru.com</a> with a goal to start selling web pages. In reality, this company ended up being a channel for me to sell my time on construction.</li>
      <li>Currently I am renting myself out as a low level manager, organizing day to day work of a 9 man scaffolding team.</li>
    </ul>

  </div>
</template>

<script>
import ExpElement from './ExpElement.vue'

  export default{
    components: {
      ExpElement
    },
    data(){
      return{
        experiences: [
          {
          facility: 'Test1',
          date: "89844",
          paragraphs: ['adsaf', 'dsfdf'],
          list: ['bullet 1', 'nullet 2']
          },
          {
          facility: 'Test2',
          date: "89844",
          paragraphs: ['adsaf', 'dsfdf'],
          list: ['bullet 1', 'nullet 2']
          },
        ],
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


<style scoped>
.experience {
  padding-bottom: 5vh;
}

.experience h3 {
  padding: 0;
  margin: 0;
}

.experience h4 {
  padding: 0;
  margin: 0;
}

.experience ul {
  padding-top: 1vh;
  margin: 0;
}

.experience li {
  padding: 0;
  margin: 0;
}

.experience p{
  padding: 0;
  margin-top: 0;
  margin-bottom: 2vh;
}

@media (min-width:1023px){
  .experience h3 {
    font-size: 3vh;
    padding-top: 3vh;
  }

  .experience h4 {
    font-size: 3vh;
    font-weight: 400;
  }

  .experience li {
    font-size: 3vh;
  }

}
</style>
