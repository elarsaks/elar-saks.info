<template>
  <div class="content">
    <h3 v-if="exp.facility"> {{ exp.facility }} </h3>
    <h4 v-if="exp.position"> {{ exp.position }} </h4>
    <h4 v-if="exp.date"> {{ exp.date }} </h4>
    <p v-for="paragraph in exp.paragraphs" v-bind:key="paragraph">{{paragraph}}</p>
    <ul v-if="list">
      <p v-for="list in exp.list" v-bind:key="list">{{lists}}</p>
    </ul>
  </div>
</template>

<script>
  export default{
    props: ['exp'],
    data(){
      return{
        
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
