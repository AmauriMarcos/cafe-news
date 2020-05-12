<template>
  <div class="grid">
    <News></News>
    <Advertisement></Advertisement>
    <Coronavirus></Coronavirus>
    <Header></Header>
  </div>   
</template>

<script>
import News from "./components/News";
import Header from "./components/Header";
import Advertisement from "./components/Advertisement";
import Coronavirus from "./components/Coronavirus";

export default {
    components: {
      News,
      Header,
      Advertisement,
      Coronavirus
    }
};
</script>

<style lang="scss">
  .grid{
    display: grid;
    grid-template-columns: repeat(12, 1fr);
  }
</style>