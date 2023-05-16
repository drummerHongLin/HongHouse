<script>
import Marquee from "@/components/Marquee/index.vue";
import ImgCarousel from "@/components/Carousel/index.vue";
import MainContent from "@/components/MainContent/index.vue";
export default {
    name: 'Home',
  components:{Marquee,ImgCarousel,MainContent}
}
</script>
<template>
    <Marquee/>
    <div class="main-content">
      <ImgCarousel/>
      <MainContent></MainContent>
    </div>
</template>
<style>
.main-content{
  width: 80vw;
  display: flex;
  flex-direction: column;
}
</style>
