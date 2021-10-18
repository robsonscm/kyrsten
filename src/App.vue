<template>
  <Home />
</template>

<script>
import Home from "./components/Home.vue";

export default {
  name: "App",
  components: {
    Home: Home,
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  transition: all 1s;
  -webkit-animation: text-focus-in 0.7s cubic-bezier(0.215, 0.61, 0.355, 1) both;
  animation: text-focus-in 0.7s cubic-bezier(0.215, 0.61, 0.355, 1) both;
}

#app {
  font-family: "Haas Grot Text R Web", "Helvetica Neue", Helvetica, Arial,
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
  height: 100vh;

  --background-color: #000000;
  --text-color: #FFFDFF;
  --about-text-color: #7378D3;
  --explore-background-color: #3641FC;
  --stories-background-color: #FF7E2C;
  --about-background-color: #E4DFFB;
  --help-background-color: #7479D5;

  --border-radius-links: 25px;
}

@media only screen and (min-width: 960px) {
  #app {
    --border-radius-links: 40px;
  }
}

@-webkit-keyframes text-focus-in {
  0% {
    -webkit-filter: blur(12px);
    filter: blur(12px);
    opacity: 0;
  }
  100% {
    -webkit-filter: blur(0px);
    filter: blur(0px);
    opacity: 1;
  }
}
@keyframes text-focus-in {
  0% {
    -webkit-filter: blur(12px);
    filter: blur(12px);
    opacity: 0;
  }
  100% {
    -webkit-filter: blur(0px);
    filter: blur(0px);
    opacity: 1;
  }
}
</style>
