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
      @change-content="openCloseContent"
    />
    <Desktop
      :open="open"
      :content="content[sectionContent]"
      v-if="windowWidth >= 1023"
    />
    <div id="mobile" v-if="open && windowWidth < 1023" >
      <Section 
        v-for="(item, index) in content" v-bind:key="index"
        :index="index"
        :item="item"
        :section="sectionContent"
        @change-content="openCloseContent"
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
    openCloseContent(selected){
      if (this.windowWidth < 1023){
        this.sectionContent = this.sectionContent == selected ? false : selected
      } else {
        this.sectionContent = selected
      }
      console.log(selected, this.sectionContent)
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
    this.sectionContent = this.windowWidth < 1023 ? '' : 'about'
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
  overflow: hidden;
  overflow-y: scroll;
}

#app {
  min-height: 100vh;
  font-family: Roboto;
  padding-bottom: 5vh;
}

#mobile{
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
  #mobile {
    width: 70vw;
    overflow-y: scroll;
  }
}

@media (min-width:1023px){

  #app {
    overflow: hidden;
  }

  #mobile {
    display: none;
  }


}

</style>
