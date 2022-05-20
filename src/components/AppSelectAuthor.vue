<template>
  <select
    class="form-select"
    v-model="author"
    @change="$emit('selectAuthorChange', author)"
    aria-label="Default select example"
  >
    <option value="">All</option>
    <option v-for="(item, index) in disksAuthor" :key="index" :value="item">
      {{ item }}
    </option>
  </select>
</template>

<script>
export default {
  name: "AppSelectAuthor",
  props: {
    disks: Array,
  },
  data() {
    return {
      author: "",
      disksAuthor: [],
    };
  },
  methods: {
    authorList() {
      this.disks.forEach((item) => {
        if (!this.disksAuthor.includes(item.author)) {
          this.disksAuthor.push(item.author);
        }
        return this.disksAuthor;
      });
    },
  },
  created() {
    this.authorList();
  },
};
</script>

<style lang="scss" scoped></style>
