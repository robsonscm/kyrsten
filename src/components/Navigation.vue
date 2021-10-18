<template>
  <nav class="navigation">
    <button
      class="navigation__search"
      @click="closeContent()"
      v-html="searchSvg"
    ></button>
    <ul
      class="navigation__list"
      v-for="(link, index) in linksContent"
      :key="index"
    >
      <li
        class="navigation__list-item"
        :class="
          link.headline && currentContent === link.headline.toLowerCase()
            ? 'navigation__list-item--active'
            : ''
        "
        @click="
          changeContent(link.headline ? link.headline.toLowerCase() : 'landing')
        "
      >
        {{ link.headline || "" }}
      </li>
    </ul>
  </nav>
</template>

<script>
import searchSvg from "../assets/search.svg";
export default {
  name: "Navigation",
  props: {
    currentContent: String,
    linksContent: String,
  },
  data: function () {
    return {
      searchSvg,
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
.navigation__search {
  background-color: transparent;
  stroke: var(--text-color);
  border: none;
  padding: 0 1em;
  animation: none;
  transition: none;
}

.home.about .navigation__search {
  stroke: var(--about-text-color);
}

.navigation__search svg {
  width: 16px;
  height: 10px;
}

.navigation__list {
  display: inline;
}

.navigation__list-item {
  list-style-type: none;
  padding: 0 0.5em;
  display: inline;
  font-size: 0.5em;
}

.home.about .navigation__list-item {
  color: var(--about-text-color);
}

.navigation__list-item--active {
  text-decoration: underline;
}

.navigation__list-item:hover {
  text-decoration: underline;
}

@media only screen and (min-width: 960px) {
  .navigation {
    width: 100%;
    position: absolute;
  }
}
</style>
