<template>
  <div id="app">
    <nav>
      <router-link to="/login">Login</router-link>
      <router-link to="/">Home</router-link>
    </nav>
    showProcess-{{ showProcess }}
    <component :is="layout">
      <router-view />
    </component>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "App",
  computed: {
    ...mapState(["showProcess"]),
    layout() {
      const layoutName = this.$route.meta.layout || "default";
      const title = this.$route.meta.title || this.$route.name;
      this.$meta.setDocumentTitle(title);
      return () => import(`@/layout/${layoutName}.vue`);
    },
  },
};
</script>

<style lang="scss"></style>
