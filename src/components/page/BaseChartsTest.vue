<template>
  <div>
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-date"></i> 图表</el-breadcrumb-item>
        <el-breadcrumb-item>基础图表</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="piewrap">
      <div class="inner">
        <!-- <div class="ileft" :style="['transform: rotate(' + LeftDushu + 'deg);']"></div> -->
        <div class="ileft" :style="{transform:'rotate(' +(LeftDushu)+'deg)',WebkitTransform:'rotate(' +(LeftDushu)+'deg)'}"></div>
        <!-- <div class="iright" :style="['transform: rotate(' + rightDushu + 'deg);']"></div> -->
        <div class="iright" :style="{transform:'rotate(' +(rightDushu)+'deg)',WebkitTransform:'rotate(' +(rightDushu)+'deg)'}"></div>
        <div class="masker" v-show="isShowMasker"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShowMasker: false,
      use: 60000,
      unuse: 30000,
      LeftDushu: 0,
      rightDushu: 0
    }
  },
  created () {
    let all = this.use + this.unuse; // 赋值2
    let radio = this.use/all;
    this.rightDushu = 360 * radio;
    if(radio > 0.5) {
      this.isShowMasker = true;
      this.LeftDushu = this.rightDushu - 180
      console.log(`LeftDushu:${this.LeftDushu}`)
    }
    console.log(radio)
    console.log(all)
    console.log(`rightDushu:${this.rightDushu}`)
  }
}
</script>

<style scoped lang="scss">
$blueColor: #2D6DEB;
$whiteColor: #ffffff;
.piewrap {
  position: relative;
  .inner {
    position: absolute;
    width: 138px;
    height: 138px;
    border-radius: 140px;
    overflow: hidden;
    left: 13px;
    top: 13px;
    background-color: $blueColor;
    border: 1px solid #c7c7c7;
    .ileft,
    .iright,
    .masker {
      position: absolute;
      width: 50%;
      height: 100%;
    }
    .ileft {
      left: 0;
      top: 0;
      background-color: $whiteColor;
      transform-origin: right center;
    }
    .iright {
      left: 50%;
      top: 0;
      background-color: $whiteColor;
      // transform: rotate(190deg);
      transform-origin: left center;
    }
    .masker {
      background-color: $blueColor;
      left: 50%;
      top: 0;
    }
  }
}

@keyframes spin {
  0% {
    transform: rotate(360deg);
  }
  100% {
    transform: rotate(0deg);
  }
}

@keyframes second-half-hide {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}

@keyframes second-half-show {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}
</style>