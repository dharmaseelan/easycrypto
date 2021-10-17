<template>
  <section id="sub_banner">
    <h1 class="title is-1">Crypto Live Rates</h1>
    <img alt="curve" src=".././assets/curve.svg" class="curve" />
  </section>
</template>

<script>
export default {
  name: "SubBanner",
};
</script>

<style lang="scss">
#sub_banner {
  position: relative;
  width: 100%;
  height: 300px;
  background-image: url(.././assets/banner_default.jpg);
  .title {
    position: absolute;
    color: $bg-color;
    font-weight: 800;
    @include center;
    top: 57%;
  }
  .curve {
    position: absolute;
    width: 100%;
    bottom: 0;
  }
  @media (max-width: 768px) {
    .title.is-1 {
      font-size: 1.7rem;
      width: 80%;
      text-align: center;
    }
  }
}
</style>
