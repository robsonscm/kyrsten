<template>
  <section class="links">
    <template v-for="(link, index) in linksContent" :key="index">
      <div
        @click="
          changeContent(link.headline ? link.headline.toLowerCase() : 'landing')
        "
        class="links__link"
        :class="[link.headline ? link.headline.toLowerCase() : '']"
      >
        <div
          class="links__link-arrow"
          v-html="arrowImage"
          v-if="link.headline && currentContent !== link.headline.toLowerCase()"
        ></div>
        <h3 class="links__link-headline">{{ link.headline || "" }}</h3>
        <p class="links__link-sub-headline" v-if="link.headline">
          {{ link.subHeadline || "" }}
        </p>
      </div>
    </template>
  </section>
</template>

<script>
import arrowImage from "../assets/arrow-up-right.svg";
export default {
  name: "Links",
  props: {
    currentContent: String,
    linksContent: String,
  },
  data: function () {
    return {
      arrowImage,
    };
  },
  components: {},
  methods: {
    changeContent: function (clickedComponent) {
      this.$emit("update-display", clickedComponent);
    },
  },
};
</script>


<style>
.links {
  height: 50%;
  width: 100%;
  margin: 0;
  display: grid;
  grid-template-columns: 50% auto;
  grid-template-rows: 50% auto;
}

.links__link {
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: end;
  padding: 1em;
  color: var(--text-color);
  height: 100%;
}

.links__link:hover .links__link-headline {
  text-decoration: underline;
}

.links__link-arrow {
  flex-grow: 1;
  align-self: self-end;
  stroke: var(--text-color);
}

.links__link-headline {
  font-size: 1.5em;
  margin-bottom: 0.5em;
  font-weight: 400;
}

.links__link-sub-headline {
  height: 30%;
  font-size: 0.75em;
}

.links__link.explore {
  background-color: var(--explore-background-color);
  border-radius: var(--border-radius-links) 0 0;
}

.links__link.stories {
  background-color: var(--stories-background-color);
  border-radius: 0 var(--border-radius-links) 0 0;
}

.links__link.about {
  --text-color: #7375C5;

  background-color: var(--about-background-color);
  border-radius: 0 0 0 var(--border-radius-links);
}

.links__link.help {
  background-color: var(--help-background-color);
  border-radius: 0 0 var(--border-radius-links) 0;
}

@media only screen and (min-width: 500px) {
  .links__link {
    padding: 1.5em;
  }

  .links__link-headline,
  .links__link-sub-headline {
    max-width: 75%;
  }

  .links__link-sub-headline {
    font-size: 0.75em;
    height: unset;
  }
}

@media only screen and (min-width: 600px) {
  .links__link-headline {
    font-size: 1.65em;
  }
}

@media only screen and (min-width: 960px) {
  .links {
    height: unset;
    width: 50%;
  }

  .links__link {
    padding: 2em;
  }
}
</style>
