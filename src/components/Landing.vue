<template>
  <div class="landing" v-if="currentContent === 'landing'">
    <h3 class="landing__headline">{{ landingContent.headline || "" }}</h3>
    <p class="landing__body">{{ landingContent.body || "" }}</p>
    <button
      class="landing__button"
      type="button"
      v-if="landingContent.buttonText"
    >
      {{ landingContent.buttonText }}
    </button>
  </div>
  <template v-if="currentContent !== 'landing'">
    <template v-for="link in linksContent">
      <div
        :key="[link.headline ? link.headline : '']"
        class="landing"
        :class="currentContent"
        v-if="link.headline && currentContent == link.headline.toLowerCase()"
      >
        <h3 class="landing__headline">
          {{ link.headline || "" }}
          <div
            class="landing__close"
            @click="closeContent()"
            v-html="closeSvg"
          ></div>
        </h3>
        <p class="landing__body">{{ link.body || "" }}</p>
      </div>
    </template>
  </template>
</template>

<script>
import closeSvg from "../assets/x.svg";
export default {
  name: "Landing",
  props: {
    currentContent: String,
    linksContent: String,
  },
  data: function () {
    return {
      landingContent: {
        headline: "It`s never too late to try something new",
        body:
          "Three paths lead to knowledge: the path of reflection is the noblest, the path of imitation is the eqsiest, and the path of experience is the bitterest.",
        buttonText: "book now",
      },
      closeSvg,
    };
  },
  methods: {
    closeContent: function (clickedComponent) {
      this.$emit("close-content", clickedComponent);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.landing {
  display: flex;
  flex-direction: column;
  height: 50%;
  align-items: flex-start;
  padding: 1em 1em 0.75em 1em;
}

.landing__headline,
.landing__body,
.landing__button {
  color: var(--text-color);
  margin-bottom: 16px;
}

.about .landing__headline,
.about .landing__body {
  color: var(--about-text-color);
}

.landing__headline {
  font-size: 1.75em;
  display: flex;
  justify-content: space-between;
  width: 100%;
  font-weight: 400;
}

.landing__body {
  max-height: 200px;
  overflow: scroll;
}

.landing__button {
  background-color: transparent;
  color: var(--text-color);
  border: 2px solid var(--text-color);
  padding: 1em 2.5em;
  border-radius: var(--border-radius-links);
  text-transform: capitalize;
  font-size: 0.5em;
  letter-spacing: -1px;
}

.landing__close {
  background-color: transparent;
  height: 30px;
  width: 30px;
  border: none;
  stroke: var(--text-color);
}

.landing__close:hover {
  transform: rotate(-90deg);
}

.about .landing__close {
  stroke: var(--about-text-color);
}

@media only screen and (min-width: 375px) {
  .landing {
    padding: 1.5em 1.5em 1em 1.5em;
  }
}

@media only screen and (min-width: 500px) {
  .landing__headline {
    font-size: 2em;
  }

  .landing__body {
    font-size: 1.05em;
    max-width: 400px;
  }

  .landing__button {
    font-size: 0.85em;
  }
}

@media only screen and (min-width: 960px) {
  .landing {
    height: unset;
    width: calc(50% - 2.5em);
    max-width: unset;
    padding: 4em 0 2.5em 2.5em;
  }

  .landing__headline {
    width: 100%;
    font-size: 2em;
  }

  .landing__headline,
  .landing__body {
    max-width: 75%;
  }

  .landing__body {
    max-height: unset;
  }

  .landing__headline,
  .landing__body,
  .landing__button {
    margin-bottom: 32px;
  }
}
</style>
