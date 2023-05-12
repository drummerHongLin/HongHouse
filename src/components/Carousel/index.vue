<script>
export default {
    name:'ImgCarousel',
    data(){
        return {
            imgList:[
                "./images/img1.jpg",
                "./images/img2.jpg",
            ],
            fill:'cover'
        }
    }
}
</script>
<template>
<el-carousel indicator-position="outside" height = '600px'>
    <el-carousel-item v-for="(img,index) in imgList" :key="index">
        <el-image  :src="img" :fit="fill"/>
    </el-carousel-item>
</el-carousel>
</template>
<style lang="less" scoped>
.el-carousel{
    padding:5px;
    .el-carousel__item {
    text-align: center;
}
}


 
</style>