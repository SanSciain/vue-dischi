<template>
  <div class="ms-bg overflow-auto">
    <AppLoading v-if="!flag" />
    <div
      v-else
      class="container mx-auto my-0 d-flex flex-wrap p-3 justify-content-between"
    >
      <AppDisk v-for="(item, index) in disks" :key="index" :disk="item" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AppDisk from "./AppDisk.vue";
import AppLoading from "./AppLoading.vue";
export default {
  name: "AppDisksList",
  components: {
    AppDisk,
    AppLoading,
  },
  data() {
    return {
      disks: [],
      flag: false,
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.disks = resp.data.response;
        this.flag = resp.data.success;
      });
  },
};
</script>

<style lang="scss" scoped>
.ms-bg {
  background-color: #1e2d3b;
  height: calc(100vh - 70px);
}
</style>
