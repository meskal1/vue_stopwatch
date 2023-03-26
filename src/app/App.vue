<script>
import CounterItem from "../common/components/CounterItem.vue";

export default {
  name: "App",
  components: {
    CounterItem,
  },
  data() {
    return {
      countersIDs: [],
    };
  },
  methods: {
    handleAddCounter() {
      this.countersIDs.push({ id: (this.countersIDs.length + 1).toString() });
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <div class="content">
      <CounterItem v-for="counter in countersIDs" :key="counter.id" />
      <button class="add-counter" @click="handleAddCounter">+</button>
    </div>
  </div>
</template>

<style>
@font-face {
  font-family: "GothamPro";
  font-style: normal;
  font-weight: 400;
  src: url("../common/fonts/GothamProRegular.woff2") format("woff2"),
    url("../common/fonts/GothamProRegular.woff") format("woff");
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: 0;
}

li {
  list-style: none;
}

a,
a:visited {
  text-decoration: none;
}

a:hover {
  text-decoration: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: inherit;
}

img {
  vertical-align: top;
}

html,
body {
  height: 100%;
  background: #353638;
  font-family: "GothamPro", sans-serif;
  line-height: 1;
  text-rendering: optimizeLegibility;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  /* When you tap, it removes the background rectangles */
  -webkit-tap-highlight-color: transparent;
}

html {
  font-size: 22px;
  color: white;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New",
    monospace;
}

#app {
  overflow: hidden;
  display: flex;
  flex-direction: column;
  min-height: 100%;
}

.wrapper {
  width: 100%;
  max-width: 1050px;
  margin: auto;
  padding: 20px 15px;
}
.content {
  margin: 0 auto;
  max-width: 775px;
  row-gap: 45px;
  column-gap: 50px;
  display: grid;
  grid-template-columns: repeat(auto-fill, 225px);
  justify-content: center;
}
.add-counter {
  display: flex;
  flex-direction: column;
  flex: 0 1 225px;
  background: #696969;
  min-height: 120px;
  color: #9e9e9e;
  align-items: center;
  justify-content: center;
  font-size: 39px;
  line-height: 20px;
  cursor: pointer;
}
.add-counter:active {
  background: #4e4e4e;
}
</style>
