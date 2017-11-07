<template>
  <div>
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-date"></i> 图表</el-breadcrumb-item>
        <el-breadcrumb-item>基础图表</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="schart">
      <div class="content-title">饼状图</div>
      <schart canvasId="pie" width="500" height="400" :data="data2" type="pie" :options="options2"></schart>
    </div>
    <!-- <div class="schart">
                        <div class="content-title">环形图</div>
                        <schart canvasId="ring" width="500" height="400" :data="data2" type="ring" :options="options2"></schart>
                    </div> -->
    <canvas ref="myCanvas" width="200px" height="150px" style="border: 1px solid red;">
      您的浏览器不支持canvas标签。
    </canvas>
  </div>
</template>

<script>
import Schart from 'vue-schart';
export default {
  components: {
    Schart
  },
  data: () => ({
    data2: [
      { name: '已提额', value: 20000 },
      { name: '省下可提额度', value: 40000 }
    ],
    options2: {
      title: '您当前已提额：20000元',
      colorList: ['#646464','#FF4949'],
      legendColor: '#000000',         // 图例文本颜色
      legend: '#000000',         // 图例文本颜色
      titleColor: '#646464',
      fillColor: '#72f6ff'
    }
  }),
  created() {

    //获取Canvas对象(画布)
    var canvas = this.$refs.myCanvas;
    //简单地检测当前浏览器是否支持Canvas对象，以免在一些不支持html5的浏览器中提示语法错误
    if (canvas.getContext) {
      //获取对应的CanvasRenderingContext2D对象(画笔)
      var ctx = canvas.getContext('2d');

      //开始一个新的绘制路径
      ctx.beginPath();
      //设置弧线的颜色为蓝色
      ctx.strokeStyle = "blue";
      ctx.fillStyle = '#FF0000';
      var circle = {
        x: 100,    //圆心的x轴坐标值
        y: 100,    //圆心的y轴坐标值
        r: 50      //圆的半径
      };
      //沿着坐标点(100,100)为圆心、半径为50px的圆的顺时针方向绘制弧线
      ctx.arc(circle.x, circle.y, circle.r, 0, Math.PI / 2, false);
      //按照指定的路径绘制弧线
      ctx.lineTo(100, 100);
      ctx.closePath();
      ctx.stroke();
      ctx.fill();
    }


  }
}
</script>

<style scoped>
.schart {
  width: 600px;
  display: inline-block;
}

.content-title {
  clear: both;
  font-weight: 400;
  line-height: 50px;
  margin: 10px 0;
  font-size: 22px;
  color: #1f2f3d;
}
</style>