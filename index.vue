<template>
  <div>
    <div id="myChart" :style="{width: '300px', height: '400px'}"></div>
    <circlemoon :dom="dom" v-model="show" ref="circlemoon">
      <div slot="header" class="ctop">
        <div class="top_left">
          <span style="display:flex;align-items:center;" @click="show = false"><svg t="1637561746590" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2450" width="16" height="16"><path d="M939.880137 487.72513l-782.215258 0 358.804922-318.92975c12.389168-11.011798 13.505595-29.980825 2.492774-42.369993-11.011798-12.386098-29.977755-13.505595-42.367947-2.492774L64.602344 490.13911c-6.407943 5.693676-10.073426 13.858636-10.073426 22.430872s3.665483 16.737196 10.073426 22.430872l411.993309 366.204449c5.717212 5.083785 12.83533 7.580652 19.925818 7.580652 8.274454 0 16.514115-3.403516 22.442128-10.07445 11.011798-12.387122 9.896394-31.357172-2.492774-42.367947L169.687704 548.100196 939.880137 548.100196c16.57449 0 30.011524-13.613042 30.011524-30.187533S956.454628 487.72513 939.880137 487.72513z" p-id="2451"></path></svg></span>
          <span>圈阅</span>
        </div>
        <div class="top_right" @click="save">完成</div>
      </div>
    </circlemoon>
    <div @click="show = true">
      展示弹出层
    </div>
    <!-- <photo-editor :dom="dom" v-model="show" v-if="show"></photo-editor> -->
  </div>
</template>

<script>
// let echarts = require('echarts/lib/echarts')
// // 引入柱状图组件
// require('echarts/lib/chart/bar')
// require('echarts/lib/component/tooltip')
// require('echarts/lib/component/title')
import circlemoon from './circlemoon'
export default {
  name: "index",
  components: {
    circlemoon
  },
  directives: {
  },

  data() {
    return {
      dom:null,
      show:false
    };
  },

  mounted() {
        this.init()
  },

  methods: {
    save(){
      let data = this.$refs.circlemoon.save()
      console.log(data);
    },
    init(){
      let dom = document.getElementById('myChart')
      let myChartinit = this.$echarts.init(dom)
        // 绘制图表
      myChartinit.setOption({
        title: { text: '在Vue中使用echarts' },
        tooltip: {},
        xAxis: {
            data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
        },
        yAxis: {},
        series: [{
            name: '销量',
            type: 'bar',
            data: [5, 20, 36, 10, 10, 20]
        }]
      });
      this.dom = dom
    }
  },
};
</script>

<style lang="scss">
.ctop{
  display: flex;
  justify-content: space-between;
  margin-top:15px;
  font-size: 32px;
  font-weight: 700;
  .top_left{
    padding: 3px 6px;
    display:flex;
    align-items:center;
    margin-top:0;
    span{
      margin-right:10px;
    }
  }
  .top_right{
    padding: 3px 6px;
    color:#409EFF;
  }
}
</style>