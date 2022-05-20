<template>
  <select
    class="form-select"
    v-model="genre"
    @change="$emit('selectChange', genre)"
    aria-label="Default select example"
  >
    <option value="">All</option>
    <option v-for="(item, index) in disksGenre" :key="index" :value="item">
      {{ item }}
    </option>
  </select>
</template>

<script>
export default {
  name: "AppSelect",
  props: {
    disks: Array,
  },
  data() {
    return {
      genre: "",
      disksGenre: [],
    };
  },
  methods: {
    genreList() {
      this.disks.forEach((item) => {
        if (!this.disksGenre.includes(item.genre)) {
          this.disksGenre.push(item.genre);
        }
        return this.disksGenre;
      });
    },
  },
  created() {
    this.genreList();
  },
};
</script>

<style lang="scss" scoped></style>
