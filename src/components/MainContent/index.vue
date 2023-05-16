<script>
import IndexDisplay from "@/components/MainContent/IndexDisplay/index.vue";
import NewsContent from "@/components/MainContent/NewsContent/index.vue";
export default {
  name:"MainContent",
  components:{IndexDisplay,NewsContent}
}
</script>
<template>
  <div class="content-container">
    <IndexDisplay/>
    <NewsContent/>
  </div>
</template>
<style lang="less">
.content-container {
  width: 60vw;
  height: 600px;
  display: flex;
  flex-direction: column;
}
</style>
