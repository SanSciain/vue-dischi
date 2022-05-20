<template>
  <div class="ms-bg overflow-auto">
    <AppLoading v-if="!flag" />
    <div
      v-else
      class="container mx-auto my-0 d-flex flex-wrap p-3 justify-content-between"
    >
      <div class="row w-100 my-3">
        <div class="col">
          <AppSelectGenre
            @selectGenreChange="disksSelectedByGenre($event)"
            :disks="disks"
          />
        </div>
        <div class="col">
          <AppSelectAuthor
            @selectAuthorChange="disksSelectedByAuthor($event)"
            :disks="disks"
          />
        </div>
      </div>

      <div class="row row-cols-5 w-100 gx-4 gy-3">
        <div v-for="(item, index) in disksFiltered" :key="index" class="col">
          <AppDisk :disk="item" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AppDisk from "./AppDisk.vue";
import AppLoading from "./AppLoading.vue";
import AppSelectGenre from "./AppSelectGenre.vue";
import AppSelectAuthor from "./AppSelectAuthor.vue";
export default {
  name: "AppDisksList",
  components: {
    AppDisk,
    AppLoading,
    AppSelectGenre,
    AppSelectAuthor,
  },
  data() {
    return {
      disks: [],
      flag: false,
      genre: "",
      author: "",
      disksFiltered: [],
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.disks = resp.data.response;
        this.flag = resp.data.success;
        this.disksSelectedByGenre(this.genre);
        this.disksSelectedByAuthor(this.author);
      });
  },
  methods: {
    disksSelectedByGenre(genreChoose) {
      const disksMatching = this.disks.filter((item) => {
        return item.genre.includes(genreChoose);
      });
      this.disksFiltered = disksMatching;
    },
    disksSelectedByAuthor(authorChoose) {
      const disksMatching = this.disks.filter((item) => {
        return item.author.includes(authorChoose);
      });
      this.disksFiltered = disksMatching;
    },
  },
};
</script>

<style lang="scss" scoped>
.ms-bg {
  background-color: #1e2d3b;
  height: calc(100vh - 70px);
}
</style>
