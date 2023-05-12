<template>
    <div class="marquee-container">
      <div class="marquee-box" ref="temp">
        <div v-for="(v,i) in list1" :key="v + '1'" class="marquee-li">
          <span class="marquee-item-title">{{ i+1}}.</span> <span class="marquee-item-content">{{v}}</span>
        </div>
        <div v-for="(v,i) in list2" :key="v + '2'" class="marquee-li">
          <span class="marquee-item-title">{{ i+1}}.</span> <span class="marquee-item-content">{{v}}</span>
        </div>
        <div v-for="(v,i) in list3" :key="v + '2'" class="marquee-li">
          <span class="marquee-item-title">{{ i+1}}.</span> <span class="marquee-item-content">{{v}}</span>
        </div>
      </div>
    </div>
</template>

<script>
let x = 0;
export default {
  name:"Marquee",
  data() {
    return {
      tempInterval: undefined,
      list1:[
        '长沙橘子洲', '长沙岳麓山', '长沙五一广场', '长沙博物馆',
      ],
      list2:[
        '成都春熙路', '成都龙泉山', '成都天府广场', '成都博物馆',
      ],
      list3:[
        '广州春熙路', '广州龙泉山', '广州天府广场', '广州博物馆',
      ]
    };
  },
  components: {},
  computed: {},
  unmounted() {
    clearInterval(this.tempInterval);
  },
  mounted() {
    this.tempInterval = setInterval(this.rollTemp, 100);
  },
  methods: {
    rollTemp() {
      let all = 0;
      let count = this.$refs.temp.childElementCount;
      for (let i = 0; i < count; i++) {
        all += this.$refs.temp.children[i].offsetWidth;
      }

      let half = all*2 / 3 ;

      if (x < 1 - half) {
        x = 0;
      }
      x -= 2;
      this.$refs.temp.style.transform = "translateX(" + x + "px)";
    }
  }
};
</script>
<style scoped lang="less" >
.marquee-container {
  position: fixed;
  top: 50px;
  z-index: 1000;
  background-color: white;
  color: #606266;
  font-size: 20px;
  width: 80vw;
  height: 40px;
  line-height: 40px;
  border-bottom: 1px solid #909399;
  overflow: hidden;
  .marquee-box {
    white-space: nowrap;
    .marquee-li {
      display: inline;
      height: 30px;
      padding-right: 20px;
    }
  }
}
</style>
