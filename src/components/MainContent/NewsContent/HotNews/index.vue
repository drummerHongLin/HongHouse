<script>
export default {
    name:"HotNews",
    data(){
        return{
            count:20,
            loading:false
        }
    },
    methods:{
        hotload(){

            this.count +=2
            ,this.loading = false
        }
    }
}
</script>
<template>
<ul v-infinite-scroll="hotload" class="infinite-list" style="overflow: auto" infinite-scroll-disabled="loading">
    <li v-for="i in count" :key="i" class="infinite-list-item">{{ i }}</li>
</ul>
</template>
<style lang="less" scoped>
</style>