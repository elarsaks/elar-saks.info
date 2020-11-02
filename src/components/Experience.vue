<template>
  <div class="content experience">
    <h3>MuruPuru OY</h3>
    <h4>Owner / Freelance Web Developer</h4>
    <h4>01/2017 – Present </h4>
    <p> Murupuru OY is a side project to fund my studies and hobby projects. Although most of its
    revenue has come from construction, it has also provided me with the opportunity to build out 2
    websites that are up still today: <a @click="link(murupuru)" >www.murupuru.com</a>  and <a @click="link(lauttasaarensiivous)"> www.lauttasaarensiivous.fi </a>.</p>

    <h3>Nord Property </h3>
    <h4>Real Estate Broker intern</h4>
    <h4>05/2014 – 07/2014</h4>
    <p> Developed sales strategies for real estate in Estonia and Finland. Built a network of sellers and
    buyers, creating opportunities for potential transactions. </p>

    <h3>Estonian Defence Forces </h3>
    <h4>Sergeant (Infantry)</h4>
    <h4>06/2011 – 05/2012</h4>
    <p> Became a Platoon Commander and Wartime Officer from a 2% selection rate. Managed a
    platoon of 26 soldiers through field training and on-base education. Supervised the maintenance
    and acquisition of equipment including trucks, weapons, and spare parts </p>

  </div>
</template>

<script>
  export default{
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
.experience h3 {
  padding: 0;
  margin: 0;
}

.experience  h4 {
  padding: 0;
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
</style>
