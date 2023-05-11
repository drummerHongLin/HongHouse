<template>
  <div>
    <div class="scroll-temp">
      <div class="temp-box" ref="temp">
        <div v-for="(v,i) in list1" :key="v + '1'" class="li">
          {{ i+1}}. {{v}}
        </div>
        <div v-for="(v,i) in list2" :key="v + '2'" class="li">
          {{ i+1}}. {{v}}
        </div>
        <div v-for="(v,i) in list3" :key="v + '2'" class="li">
          {{ i+1}}. {{v}}
        </div>
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
.scroll-temp {
  background:pink;
  color: #000;
  font-size: 20px;
  top: 100px;
  left: 480px;
  width: 960px;
  height: 30px;
  line-height: 30px;
  overflow: hidden;
  .temp-box {
    white-space: nowrap;
    .li {
      display: inline;
      height: 30px;
      padding-right: 20px;
    }
  }
}
</style>
