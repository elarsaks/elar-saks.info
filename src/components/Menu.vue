<template >
  <div class="menu" :class="[ open ? 'menu' : 'menu-open' ]">
    <div id="menu-header" @click="openSlogan()">
      <h1>MENU</h1>
    </div>

    <div class="menu-items">
      <h4 
        v-for="(item, index) in content" v-bind:key="index" 
        class="menu-item" 
        @click="$emit('change-content', index)"
        >{{item.header}}</h4>
    </div>
  </div>
  
</template>

<script>
  export default{
    props: ['content', 'open', 'openSlogan'],
    componentDidMount() {
      this.$emit('change-content', 'About')
    }
  }
</script>

<style>
#menu-header {
  width: 100%;
  border-bottom: 1px solid white;
  height: 11vh;
}

#menu-header :hover {
  cursor: pointer;
}

.menu {
  position: absolute;
  top: 0px;
  right: 0px;
  z-index: 99;
  height: 100vh;
  width: 15vw;
  background-color: rgba(0, 0, 0, 0.3);
  color: white;
  -webkit-transition: all 2s;
  transition: all 2s;
}

.menu-open {
  right: -20vw;
  z-index: 99;
  -webkit-transition: all 2s;
  transition: all 2s;
}

.menu h1 {
  font-weight: 400;
  font-size: 6vh;
  padding-left: 10px;
}

.menu h4 {
  font-weight: 400;
  font-size: 3vh;
  padding: 10px;
}

.menu-item {
  font-weight: 300;
  font-size: 3vh;
  padding-left: 10px;
}

.menu-items :hover {
  cursor: pointer;
  font-weight: 400;
}
</style>