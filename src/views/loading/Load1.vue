<template>
  <div>
    <h3>load1</h3>
    <div ref="zrender" id="zrender" class="zrender"></div>
  </div>
</template>

<script>
import * as zrender from 'zrender/dist/zrender.js';
export default {
  name: 'load1',
  data() {
    return {
      group: {},
      zr: {},
      rect: {}
    }
  },
  mounted() {
    this.zRenderInit();
    // this.group.animate()
    // .when(1000, {
    //     x: 100,
    // })
    // .when(1000, {
    //     rotation : 15,
    //     originX: 250,
    //     originY: 250,
    // })
    // .when(1500, {
    //   scaleX: 0.5,
    //   scaleY: 0.5,
    //   originX: 250,
    //   originY: 250,
    // })
    // .start();
  },
  methods: {
    /**初始化 zRender */
    zRenderInit() {
      let dom = this.$refs.zrender;
      this.zr = zrender.init(dom);
      // this.group = new zrender.Group();
      // this.group.x = 250;
      // this.group.y = 250;
      // this.drawTrochoid();
      // this.zr.add(this.group);
      let option = {
          style:{
              fill:'red',      //填充颜色
              stroke:'none', //描边颜色
          },
          shape:{
              cx:150,           //x,y代表坐标
              cy:150,
              // width:200,
              // height:200,
              r: 150,
              // r:[3]            //圆角
          },
          z:1                   //层次，大的会覆盖小的
      }
      // 外旋轮线
      this.rect = new zrender.Circle(option);
      
      this.rect.transformCoordToGlobal(0,0)
      this.rect.animate()
      .when(2000, {
        rotation: Math.PI/2,
        originX: 150,
        originY: 150
      })
      // .when(2000,{x:0})
      // .when(3000,{y:400})
      // .when(4000,{y:200})
      .done(()=>{
        console.log('动画完成')
      })
      .start()
      this.zr.add(this.rect)
      // this.rect.transformCoordToGlobal(200,200)
      // this.rect.animateTo({
      //     rotation: 120,         //正值代表逆时针旋转，负值代表顺时针旋转
      //     originX:200,            //设置变换中心
      //     originY:200,            //设置变换中心
      // }, 1000, 100,'linear',function(){
      //   console.log('动画完成')
      // })
    },
  }
}
</script>

<style lang='less' scoped>
#zrender {
  width: 500px;
  height: 500px;
  border: 1px solid red;
  margin: 0 auto;
}
</style>