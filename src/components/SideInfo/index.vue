<script>
export default{
    name:'SideInfo',
    data(){
        return{
            tableData:[
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
]
        }
    }
}
</script>
<template>
    <el-affix  :offset="95">
    <el-table :data="tableData" stripe style="width: 20vw;padding-left: 5px;">
    <el-table-column prop="date" label="Date"  />
    <el-table-column prop="name" label="Name" />
    <el-table-column prop="address" label="Address" />
  </el-table>
</el-affix>
</template>
<style>

</style>