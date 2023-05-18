<script>
import FirstNews from './FirstNews/index.vue'
import HotNews from './HotNews/index.vue'
export default {
  name:"NewsContent",
  data(){
      return {
        activeName:'hot'
      }
  },
  methods:{
    handleClick(tab,event){
      console.log(tab, event)
    }
  },
  components:{FirstNews,HotNews}
}
</script>
<template>
  <div class="NewsContent">
    <el-tabs v-model="activeName" class="Titles" @tab-click="handleClick">
      <el-tab-pane class="NewsMain" label = 'HotNews' name="hot">热点新闻</el-tab-pane>
      <el-tab-pane class="NewsMain" label = 'FirstNews' name="first"><FirstNews/></el-tab-pane>
    </el-tabs>
  </div>
</template>
<style lang="less">
.NewsContent {
  ::-webkit-scrollbar { width: 0 !important }
  overflow: none;
  .infinite-list-item{
    padding: 1px 0;
  }
}

</style>
