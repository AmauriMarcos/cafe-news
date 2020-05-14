<template>
  <div class="grid">
    <News></News>
    <Carousel></Carousel>
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
import Carousel from "./components/Carousel";


export default {
    components: {
      News,
      Header,
      Advertisement,
      Coronavirus,
      Carousel
    }
};
</script>

<style lang="scss">

  *{
   font-family: 'Montserrat', sans-serif;
  }

  .grid{
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    column-gap: 20px;
  }
</style>