<template>
  <div class="card ms-card-bg">
    <img :src="disk.poster" class="card-img-top p-3" :alt="disk.title" />
    <div class="card-body text-center">
      <h5 class="card-title text-uppercase">{{ disk.title }}</h5>
      <p class="card-text m-0 mt-2 ms-card-text">{{ disk.author }}</p>
      <p class="card-text ms-card-text">{{ disk.year }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppDisk",
  props: {
    disk: Object,
  },
};
</script>

<style lang="scss" scoped>
.ms-card-bg {
  background-color: #2e3a46;
  color: white;
  // width: calc(100% / 5.9);
  height: 100%;

  .ms-card-text {
    color: lightgray;
    font-size: 0.8rem;
  }
}
</style>
