<template>
  <div class="ms-bg">
    <div
      class="container mx-auto my-0 d-flex flex-wrap p-3 justify-content-between"
    >
      <AppDisk v-for="(item, index) in disks" :key="index" :disk="item" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AppDisk from "./AppDisk.vue";
export default {
  name: "AppDisksList",
  components: {
    AppDisk,
  },
  data() {
    return {
      disks: [],
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.disks = resp.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
.ms-bg {
  background-color: #1e2d3b;
}
</style>
