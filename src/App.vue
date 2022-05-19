<template>
  <div id="app">
    <AppHeader />
    <AppDisksList />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppDisksList from "./components/AppDisksList.vue";
export default {
  name: "App",
  components: {
    AppHeader,
    AppDisksList,
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
