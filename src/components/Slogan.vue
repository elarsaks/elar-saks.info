<template>
  <div>
    <div
      class="slogan"
      @click="openSlogan()"
      :class="[sloganUp ? 'sloganUp' : 'sloganDown']"
    >
      <h1>ELAR SAKS</h1>
      <h4>Junior web developer</h4>
    </div>
  </div>
</template>

<script>
export default {
  props: ["sloganUp", "openSlogan"]
};
</script>

<style>
.slogan {
  width: 98vw;
  color: #fff;
  background: transparent;
  text-align: center;
  text-transform: uppercase;
  font-family: Roboto;
  font-weight: 200;
  transform: rotate(0deg);
  z-index: 10;
  padding-bottom: 20vh;
  padding-top: 45vh;
  -webkit-transition: all 2s;
  transition: all 2s;
  cursor: pointer;
}

.slogan h1 {
  font-size: 10vw;
  font-family: Roboto;
  font-weight: 200;
  margin: 0;
  -webkit-transition: font-size 2s;
  transition: font-size 2s;
}

.slogan h4 {
  font-size: 4.3vw;
  font-family: Roboto;
  font-weight: 200;
  margin: 0;
  -webkit-transition: all 2s;
  transition: all 2s;
}

.sloganUp {
  padding-top: 0;
  padding-bottom: 2vh;
  width: 40vw;
  margin: 0;
  -webkit-transition: all 2s;
  transition: all 2s;
}

.sloganUp h1 {
  padding-top: 3vh;
  font-size: 7vw;
  -webkit-transition: all 2s;
  transition: all 2s;
}

.sloganUp h4 {
  font-size: 3vw;
  -webkit-transition: all 2s;
  transition: all 2s;
}

@media (min-width: 600px) {
  .sloganUp {
    padding-left: 12vw;
    -webkit-transition: all 2s;
    transition: all 2s;
  }
}

@media (min-width: 1023px) {
  .sloganUp {
    margin-top: 70vh;
    margin-left: -13vw;
    width: 30vw;
    min-width: 400px;
    height: 100px;
    transform: rotate(-90deg);
  }

  .sloganUp h1 {
    font-size: 5vw;
    -webkit-transition: all 2s;
    transition: all 2s;
    font-weight: 300;
  }

  .sloganUp h4 {
    font-weight: 200;
    font-size: 2.15vw;
    -webkit-transition: all 2s;
    transition: all 2s;
  }
}
</style>
