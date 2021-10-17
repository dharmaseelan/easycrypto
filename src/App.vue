<template>
  <div id="app">
    <Header />
    <SubBanner />
    <LiveRates />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import SubBanner from "./components/SubBanner.vue";
import LiveRates from "./components/LiveRates.vue";

export default {
  name: "App",
  components: {
    Header,
    SubBanner,
    LiveRates,
  },
};
</script>

<style lang="scss">
body {
  font-family: $font-family;
}
h1,
h2,
h3,
h4,
h5,
h6,
p {
  font-family: $font-family;
  color: $font-color;
}
.title {
  font-weight: 800;
  text-transform: capitalize;
  &.is-4 {
    font-weight: 800;
  }
}

@media (max-width: 999px) {
  .container {
    padding: 0 20px;
  }
}
</style>
