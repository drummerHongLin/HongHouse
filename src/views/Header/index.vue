<script>
import {Promotion} from '@element-plus/icons-vue'
export default {
    name:'Header',
    components:{Promotion}
}
</script>
<template>
    <header>
        <el-text>
            <el-icon>
                <Promotion/>
            </el-icon>
            HongHouse
        </el-text>
        <span>测试1</span>
    </header>
</template>
<style scoped lang="less">
    header{
        height: 5vh;
        min-height: 50px;
        width: 80vw;
        display: inline-flex;
        justify-content: space-between;
        align-items: center;
        border-bottom: 1px solid #909399;
        padding: 0 20px;
        .el-text {
            font-size: 30px;
        }
    }
</style>