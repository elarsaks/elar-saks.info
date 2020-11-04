<template>
  <div :class="[ open ? 'desktop-wrapper' : 'desktop-wrapper-hidden' ]">
    <h1 class="section-header">
      {{content.header}}
      <img src="./../assets/down.png" />
    </h1>
    <ExpElement 
      v-for="exp in content.content" v-bind:key="exp.facility" 
      :exp="exp" 
    />
  </div>
</template>

<script>
import ExpElement from './ExpElement.vue'

export default{
  props: ['content', 'open',],
    components: {
      ExpElement,
    },
    data(){
      return{
        murupuru: "http://www.murupuru.com",
        lauttasaarenSiivous: "http://www.lauttasaarensiivous.fi",
      }
    },
}
</script>

<style scoped>
.desktop-wrapper {
  position: absolute;
  left: 17.5vw;
  top: 15vh;
  background-color: whitesmoke;
  height: 70vh;
  width: 65vw;
  z-index: 97;
  border-radius: 15px;
  overflow-y: scroll;
  -webkit-transition: all 1.9s;
  transition: all 1.9s;
}

.desktop-wrapper-hidden {
  position: absolute;
  left: 117.5vw;
  top: 15vh;
  background-color:rgba(245, 245, 245, 0);
  height: 70vh;
  width: 65vw;
  z-index: 97;
  border-radius: 15px;
  overflow-y: scroll;
  -webkit-transition: all 1.9s;
  transition: all 1.9s;
}

h1 {
  margin-left: 2vw;
  font-size: 4vh;
  width: 95%;
  float: left;
  margin-bottom: 2vh;
}

img {
  height: 4vh;
  float: right;
}

</style>