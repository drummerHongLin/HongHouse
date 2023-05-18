<script>
export default {
    name:"FirstNews",
    data(){
        return{
            count:20,
            noMore : false
        }
    },
    methods:{
        
        //获取当前可视范围的高度
        getClientHeight() {
            var clientHeight = 0;
            if (document.body.clientHeight && document.documentElement.clientHeight) {
                clientHeight = Math.min(document.body.clientHeight, document.documentElement.clientHeight)
            } else {
                clientHeight = Math.max(document.body.clientHeight, document.documentElement.clientHeight)
            }
            return clientHeight
        },
    
        //获取文档完整的高度
        getScrollHeight() {
            return Math.max(document.body.scrollHeight, document.documentElement.scrollHeight)
        },

        //获取当前滚动条的位置
        getScrollTop() {
            var scrollTop = 0;
            //window.pageYOffset = document.documentElement.scrollTop
            if (document.documentElement && document.documentElement.scrollTop) {
                scrollTop = document.documentElement.scrollTop
            } else if (document.body) {
                scrollTop = document.body.scrollTop
            }
            return scrollTop
        },
        windowScroll() {
        //获取三个值
        var scrollTop = this.getScrollTop()
        var clientHeight = this.getClientHeight()
        var scrollHeight = this.getScrollHeight()
        console.log(scrollTop, clientHeight, scrollHeight)
        //如果满足公式则，确实到底了
        if(Math.abs(scrollTop+clientHeight - scrollHeight) <1 ){
            //发送异步请求请求数据，同时携带offset并自增offset
            //noMore是自定义变量，如果是最后一批数据则以后都不加载
            if(!this.noMore) {
                this.count +=2
            }
        }
    }

    },
    mounted(){
      console.log('我运行了一下')
      window.addEventListener('scroll', this.windowScroll,true) //监听页面滚动
    },
    beforeRouteLeave() {
	  window.removeEventListener("scroll", this.windowScroll);//销毁滚动事件
}
    
}
</script>
<template>

    <div v-for="i in count" :key="i" class="infinite-list-item">
    <el-card shadow="always">
      <template #header>
        <div class="news-card-header">
          <span class="news-card-title">第一时间</span>
          <el-button text class="news-card-more">了解更多</el-button>
        </div>
      </template>
      <el-text>{{ i }}</el-text>
    </el-card>  
    </div>

</template>
<style lang="less" scoped>

  .news-card-header{
    display: flex;
    justify-content: space-between;
    align-items:end;
    .news-card-title{
      font-size: 20px;
      font-weight: 700;
    }
  }
</style>