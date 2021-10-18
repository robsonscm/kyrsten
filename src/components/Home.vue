<template>
  <div class="home" :class="currentContent">
    <Navigation
      :currentContent="currentContent"
      :linksContent="linksContent"
      v-on:updateDisplay="updateCurrentContent($event)"
    />
    <Landing
      :currentContent="currentContent"
      :linksContent="linksContent"
      v-on:closeContent="updateCurrentContent('landing')"
    />
    <Links
      :currentContent="currentContent"
      :linksContent="linksContent"
      v-on:updateDisplay="updateCurrentContent($event)"
    />
  </div>
</template>

<script>
import Links from "./Links";
import Landing from "./Landing";
import Navigation from "./Navigation";

export default {
  name: "Home",
  data: function () {
    return {
      currentContent: "landing",
      linksContent: [
        {
          headline: "Explore",
          subHeadline: "Explore the best places deals",
          body:
            "Proin ac sollicitudin ligula. Pellentesque ultrices non nibh quis imperdiet. Vivamus ut tristique sem. ",
        },
        {
          headline: "Stories",

          subHeadline: "Our customer and Company story",
          body:
            "Etiam tincidunt neque non viverra convallis. Maecenas at nisl scelerisque, lacinia nisl vitae, dignissim felis. Donec dapibus mattis cursus. Sed aliquam finibus justo eget placerat. Maecenas accumsan dui non ipsum consectetur, sed pretium dui posuere. Ut faucibus tincidunt dui, ut cursus magna sagittis eu. Nulla sit amet dui scelerisque, fermentum purus sit amet, condimentum lorem.",
        },
        {
          headline: "About",
          subHeadline: "Our company history",
          body:
            "Vivamus aliquam tempus ullamcorper. In eleifend lorem vitae neque fermentum, ac mattis mi egestas. Quisque condimentum faucibus enim, at laoreet enim elementum eu. Vestibulum vitae sem bibendum, volutpat elit sit amet, ultrices purus.",
        },
        {
          headline: "Help",
          subHeadline: "FAQ and Support",
          body:
            "Donec ac sollicitudin sem. Suspendisse mattis nulla id eros mattis finibus. Praesent justo massa, suscipit non dapibus eget, malesuada rutrum enim. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.",
        },
      ],
    };
  },
  components: {
    Landing,
    Links,
    Navigation,
  },
  methods: {
    updateCurrentContent: function (clickedComponent) {
      this.currentContent = clickedComponent;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  border: 10px solid var(--background-color);
  background-color: var(--background-color);
  position: absolute;
  top: 5%;
  bottom: 5%;
  right: 5%;
  left: 5%;
  border-radius: 30px;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  max-height: 600px;
  max-width: 500px;
  overflow: scroll;
  min-height: 550px;
}

.home * {
  color: var(--text-color);
}

.home.explore {
  --background-color: var(--explore-background-color);
}

.home.stories {
  --background-color: var(--stories-background-color);
}

.home.about {
  --background-color: var(--about-background-color);
}

.home.help {
  --background-color: var(--help-background-color);
}

@media only screen and (min-height: 602px) {
  .home {
    margin: auto;
    height: 580px;
  }
}

@media only screen and (min-width: 960px) {
  .home {
    flex-direction: row;
    max-width: 1024px;
    border: 15px solid var(--background-color);
    border-radius: 50px;
  }
}
</style>
