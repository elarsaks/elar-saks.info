<template>
  <div 
    id="app" 
    :style="style">
    <Slogan
      v-hammer:swipe.up="onSwipeUp"
     :sloganUp="open"
     :openSlogan="openSlogan"
     />
    <Menu 
      :open="open"
      v-if="windowWidth >= 1023"
      :openSlogan="openSlogan"
      @changecontent="select"
    />
    <Desktop
      :open="open"
      v-if="windowWidth >= 1023"
      :content="content[sectionContent]"
      select="select"
    />
    <div id="wrapper" v-if="open && windowWidth < 1023">
      <Section 
        v-for="item in content" v-bind:key="item.header"
        :item="item"
        :header="item.header"
        :select="select"
        :selected="sectionContent"
      />
    </div>
  </div>
</template>

<script>
import content from './content.json'
import Desktop from './components/Desktop.vue'
import Menu from './components/Menu.vue'
import Section from './components/Section.vue'
import Slogan from './components/Slogan.vue'

let degree = 1;
let saturation = 100;
let luminosity = 20;

export default {
  name: 'app',
  components: {
    Desktop,
    Menu,
    Section,
    Slogan,
  },
  data() {
    return {
      content: content,
      open: false,
      windowHeight: window.innerHeight,
      windowWidth: window.innerWidth,
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
      console.log(header, this.sectionContent)
      this.sectionContent = this.sectionContent == header ? false : header
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
    },
    onResize() {
      this.windowHeight = window.innerHeight
    }
  },
  created() {
    setInterval(this.changeColor, 100);
    this.sectionContent = 'about'
  },
  mounted() { 
    this.$nextTick(() => {
      window.addEventListener('resize', this.onResize);
    })
  }
}
</script>

<style>

body {
  margin: 0;
  min-height: 100vh;
  font-family: Roboto;
  padding-bottom: 10vh;
}

#app {
  overflow: hidden;
  min-height: 100vh;
  font-family: Roboto;
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

@media (min-width:1023px){
  #wrapper {
    display: none;
  }
}


</style>
