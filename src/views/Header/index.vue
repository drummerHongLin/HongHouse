<script >
import {Promotion,Search} from '@element-plus/icons-vue'

export default {
name:"Header",
data() {
    return {
        searchInfo:"",
        Search,
    }
   },
components:{Promotion, Search},
methods:{
    goSearch(){ 
    console.log("我被点了一下")
    this.$router.push("/")
    }}
}
</script>
<template>
     <el-affix>
    <header>
        <div class="header-left">
            <el-text>
            <el-icon>
                <Promotion/>
            </el-icon>
            HongHouse
            </el-text>
            <el-input v-model="searchInfo" placeholder="Please Input">
                <template #append>
                <el-button :icon="Search" @click="goSearch"/>
                </template>
            </el-input>
        </div>
        <el-link>关于我们</el-link>
    </header>
</el-affix>
</template>
<style scoped lang="less">
    header{
        width: 80vw;
        height: 55px;
        background-color: white;
        display: inline-flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 1px solid #909399;
        padding: 0 20px;
        .header-left {
            display: inline-flex;
        }
        .el-input {
            width: 20vw;
            padding: 10px;
            
        }
        .el-text {
            font-size: 30px;
        }
        .el-link {
            font-size: 25px;
            .el-link .el-icon--right.el-icon {
            vertical-align: text-bottom;
            }
        }
    }
</style>