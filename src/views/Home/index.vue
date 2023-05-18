<script>
import Marquee from "@/components/Marquee/index.vue";
import ImgCarousel from "@/components/Carousel/index.vue";
import MainContent from "@/components/MainContent/index.vue";
import SideInfo from "@/components/SideInfo/index.vue";
export default {
    name: 'Home',
  components:{Marquee,ImgCarousel,MainContent,SideInfo}
}
</script>
<template>
    <Marquee/>
    <div class="main-content">
      <ImgCarousel/>
      <div class="main-info">
        <MainContent></MainContent>
        <SideInfo/>
      </div>
    </div>
</template>
<style lang="less">
.main-content{
  width: 80vw;
  display: flex;
  flex-direction: column;
  .main-info{
    display: flex;
  }
}
</style>
