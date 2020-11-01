<template>
  <div id="app" :style="style" >
    <Slogan
      v-hammer:swipe.up="onSwipeUp"
     :sloganUp="open"
     :openSlogan="openSlogan"
     />
    <div id="wrapper" v-if="open">
      <Section :select="select" :header="'About'" class="rounded-corners-up" :sectionContent="sectionContent"  />
      <Section :select="select" :header="'Projects'" :sectionContent="sectionContent" />
      <Section :select="select" :header="'Education'" :sectionContent="sectionContent"/>
      <Section :select="select" :header="'Experience'" :sectionContent="sectionContent" />
      <Section :select="select" :header="'Volunteering'" :sectionContent="sectionContent"/>
      <Section :select="select" :header="'Contact'" class="rounded-corners-down" :sectionContent="sectionContent"/>
    </div>
  </div>
</template>

<script>
import Slogan from './components/Slogan.vue'
import Section from './components/Section.vue'


let degree = 1;
let saturation = 100;
let luminosity = 20;

export default {
  name: 'app',
  components: {
    Slogan,
    Section,
  },
  data() {
    return {
      open: false,
      sectionContent: '',
      style:{
        backgroundColor: '',
      },
    }
  },
  methods: {
    onSwipeUp(){
      this.open = !this.open
    },
    select(header) {
      if(this.sectionContent == undefined || this.sectionContent != header){
        this.sectionContent = header;
      } else {
        this.sectionContent = undefined;
      }
    },
    getColor() {
      if(degree > 359){
        degree = 1
      } else {
        degree++
      }
      var colorCode = 'hsl(' + degree + ', ' + saturation + '%, ' + luminosity + '%)'
      return colorCode
    },
    changeColor(){
      this.style.backgroundColor = this.getColor()
    },
    openSlogan(){
      this.open = !this.open
    }
  },
  created() {
    setInterval(this.changeColor, 70);
  },
}
</script>

<style>
#app {
  overflow: hidden;
  min-height: 100vh;
  font-family: Roboto;
  padding-bottom: 5vh;
}

#wrapper {
  border-radius: 2vh;
  background-color: rgb(0,0,0,0.2);
  margin-left: auto;
  margin-right: auto;
  width: 95vw;
}

.rounded-corners-up {
  border-radius: 2vh 2vh 0vh 0vh;
  margin-top: 0vh;
}

.rounded-corners-down {
  border-radius: 0vh 0vh 2vh 2vh;
}

@media (min-width:600px){
  #wrapper {
    width: 70vw;
  }

}


</style>
