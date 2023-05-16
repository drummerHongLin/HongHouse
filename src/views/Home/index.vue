<script>
import Marquee from "@/components/Marquee/index.vue";
import ImgCarousel from "@/components/Carousel/index.vue";
import SummaryNav from "@/components/SummaryNav/index.vue";
export default {
    name: 'Home',
  components:{Marquee,ImgCarousel,SummaryNav}
}
</script>
<template>
    <Marquee/>

    <div class="main-content">  
      <ImgCarousel/>
      <SummaryNav/>
    </div>
</template>
<style>
.main-content{

  width: 80vw;
  display: flex;
  flex-direction: column;
}
</style>
