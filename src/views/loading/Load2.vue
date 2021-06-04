<template>
  <div>
    <h3>load2</h3>
    <div ref="zr" id="zr" class="zrender"></div>
  </div>
</template>

<script>
import * as zrender from 'zrender';
export default {
  name: 'load2',
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
    zRenderInit() {

      let dom = this.$refs.zr;

      this.zr = zrender.init(dom);

      let option = {
        style:{
          fill:'red',
          stroke:'none',
        },
        shape:{
          cx:150,
          cy:150,
          rx: 35,
          ry: 50,
        },
        z:1
      }

      this.ellipse = new zrender.Ellipse(option);

      this.ellipse.attr({
        originX: 150,
        originY: 150,
      })

      this.ellipse.animate()
        .when(500, {
          rotation: Math.PI * 2
        })
        .start()
      this.zr.add(this.ellipse)
    },
  }
}
</script>

<style lang='less' scoped>
#zr {
  width: 500px;
  height: 500px;
  border: 1px solid red;
}
</style>
