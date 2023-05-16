<script>
import * as echarts from 'echarts/core';
import { GridComponent } from 'echarts/components';
import { LineChart } from 'echarts/charts';
import { UniversalTransition } from 'echarts/features';
import { CanvasRenderer } from 'echarts/renderers';

echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition]);

export default {
  name:'IndexDisplay',
  data(){
    return{
        indexData:[
          {
            indexName:"上证指数",
            xAxis:['2017-10-24', '2017-10-25', '2017-10-26', '2017-10-27'],
            type:"line",
            indexData:[20, 34, 10, 38],
            indexSum:3290.99,
            diffSum:-19.75,
            diffRate:-0.60
          },
          {
            indexName:"深证指数",
            xAxis:['2017-10-24', '2017-10-25', '2017-10-26', '2017-10-27'],
            type:"line",
            indexData:[20, 34, 10, 38],
            indexSum:3290.99,
            diffSum:-19.75,
            diffRate:-0.60
          },
          {
            indexName:"创业板数",
            xAxis:['2017-10-24', '2017-10-25', '2017-10-26', '2017-10-27'],
            type:"line",
            indexData:
              [20, 34, 10, 38],
            indexSum:3290.99,
            diffSum:-19.75,
            diffRate:-0.60
          },
        ]
    }
  },
  methods:{
    loadCharts(){
      const V = this;
      this.indexData.forEach(
          (item,index)=>{
            // 获取图表
            const chart = echarts.init(document.getElementById(`chart_${index}`));
            let option;
            option = {
              xAxis:{
                data:item.xAxis,
                show:false,
              },
              yAxis:{
                show:false,
                boundaryGap:[0,Math.min(...item.indexData)/Math.max(...item.indexData)]
              },
              series:[
                {
                  type:item.type,
                  data:item.indexData,
                  smooth:true,
                }
              ]
            };
            option&& chart.setOption(option);
          }
      )
    }
  },
  mounted() {
    this.loadCharts()
  }
}
</script>
<template>
  <div class="index-display">
    <div class="index-item" v-for="(d,index) in indexData" :key="index">
      <div class="index-title">
        <h5 class="index-title-info">{{d.indexName}}</h5>
      </div>
      <div class="index-data">
        <div class="index-today-sum">{{ d.indexSum }}</div>
        <div class="diff-show">
          {{d.diffSum}}
          (
          {{d.diffRate}}
          %)
        </div>
      </div>
      <div class="index-chart" :id="`chart_${index}`">

      </div>
    </div>
  </div>
</template>
<style lang="less" scoped>
  .index-display  {
    display: inline-flex;
    justify-content: space-between;
    padding-bottom: 10px;
    .index-item{
      &:not(:last-child){
        border-right: 1px solid #909399;
        margin-right: 5px;
      };
      width: 100%;
      .index-title{
        width: 100%;
        height: 19px;
        .index-title-info{
          font-size: 14px;
          line-height: 1.4;
          font-weight: 400;
        }
      }
      .index-data{
        display: inline-block;
        height: 56px;
        width: 33%;
        .index-today-sum{
          font-weight: 700;
          font-size: 24px;
          line-height: 1.17;
          margin: 2px 0 0;
          padding-top: 6px;
          color: #d20
        }
        .diff-show  {
          font-size: 12px;
          color: #d20
        }
      }
      .index-chart{
        display: inline-block;
        width: 67%;
        height: 56px;
        vertical-align: center;
      }
    }
  }
</style>
