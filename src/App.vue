<template>
  <div>
    <loader-comp v-if="loading" />
    <div v-else>
      <nav-bar />

      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>

      <scroll-up-comp />
    </div>
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import LoaderComp from "./components/LoaderComp.vue";
import ScrollUpComp from "./components/ScrollUpComp.vue";

export default {
  name: "App",
  components: {
    NavBar,
    LoaderComp,
    ScrollUpComp,
  },
  data() {
    return {
      loading: true,
    };
  },
  created() {
    window.onload = () => {
      setTimeout(() => {
        this.loading = false;
      }, 500);
    };
  },
};
</script>

<style>
html,
body {
  scroll-behavior: smooth;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-decoration: none;
}
:root {
  --bg-color: #2c3e50;
  --second-bg-color: #161616;
  --text-color: #fff;
  --main-color: #00ffee;
}
html::-webkit-scrollbar {
  width: 5px;
}
html::-webkit-scrollbar-track {
  background-color: var(--bg-color);
  border-radius: 5px;
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.3);
}
html::-webkit-scrollbar-thumb {
  background-color: var(--main-color);
  border-radius: 5px;
  border: 0.5px solid var(--bg-color);
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.5);
}
</style>
