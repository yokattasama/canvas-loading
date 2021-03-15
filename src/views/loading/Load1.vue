<template>
  <div>
    <h3>load1</h3>
    <div ref="zrender" id="zrender" class="zrender"></div>
  </div>
</template>

<script>
import * as zrender from 'zrender';
export default {
  name: 'load1',
  data() {
    return {
      group: {},
      zr: {},
    }
  },
  mounted() {
    this.zRenderInit();
  },
  methods: {
    /**初始化 zRender */
    zRenderInit() {
      let dom = this.$refs.zrender;
      this.zr = zrender.init(dom);
      this.group = new zrender.Group();
      this.drawTrochoid();
      this.zr.add(this.group);
    },
    /** 绘制函数 */
    drawTrochoid() {
      let option = {
        shape: {
          cx: 200,
          cy: 200,
          r: 80,
          r0: 35,
          d: 50,
          n:"out"
        },
        style: {
          fill: "transparent", // 填充颜色，默认#000
          stroke: "#000", // 描边颜色，默认null
          lineWidth: 2, // 线宽， 默认1
          text :'外旋轮曲线',
          fontSize:"25",
          textFill:"red",
        },
        hoverable: true, // default true
        draggable: true,
      };
      // 外旋轮线
      let TrochoidShape = new zrender.Trochoid(option);
      // 添加外旋轮线到group里
      this.group.add(TrochoidShape);
    },
  }
}
</script>

<style lang='less' scoped>
#zrender {
  width: 500px;
  height: 500px;
  border: 1px solid red;
}
</style>