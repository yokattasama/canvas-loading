<template>
  <div style="height: 100%;">

    <div class="example-container"></div>
  </div>
</template>

<script>
import * as zrender from 'zrender';

export default {
  name: 'firework',
  data() {
    return {
      zr: null,
      w: 0,
      h: 0,
    }
  },
  mounted() {
    let container = document.getElementsByClassName('example-container')[0];
    this.zr = zrender.init(container);

    this.w = this.zr.getWidth();
    this.h = this.zr.getHeight();

    console.log(this.w, this.h)

    this.spray(this.w / 2, this.h / 2);

    let that = this;
    setInterval(function () {
      that.spray(this.w * Math.random(), this.h * Math.random());
    }, 1000);
  },
  methods: {
    spray(x, y) {
      let cnt = 200;
      let centerTolerance = 0;
      let radius = 10;
      let particles = [];
      let duration = 3000;
      let color = Math.random() * 260;
      let maxVx = 1000 + Math.random() * 1500;
      let maxVy = 1000 + Math.random() * 1500;
      //
      let that = this;
      //
      for (let i = 0; i < cnt; ++i) {
        (function () {
          let x0 = x + centerTolerance * (Math.random() - 1);
          let y0 = y + centerTolerance * (Math.random() - 1);
          let opacity = Math.random() * 0.5 + 0.5;

          let particle = new zrender.Circle({
            shape: {
              cx: 0,
              cy: 0,
              r: radius * (0.5 + 0.5 * Math.random())
            },
            style: {
              fill: 'hsl(' + Math.floor(color + Math.random() * 100)
                + ', 80%, '
                + Math.floor(Math.random() * 40 + 40) + '%)',
              opacity: opacity
            },
            x: x0,
            y: y0,
            // position: [x0,y0],
          });
          that.zr.add(particle);
          particles.push(particle);

          particle._t = 0;
          particle._opacity = opacity;

          let animator = particle.animate('');
          let vx = (Math.random() - 0.5) * maxVx;
          let vy = (Math.random() - 1.2) * maxVy;
          let ay = 8000;
          let t0 = 0;

          animator
            .when(duration, {
              _t: 1
            })
            .during(function (p, _t) {
              let dt = _t - t0;
              let x1 = p.x + vx * dt;
              let y1 = p.y + vy * dt;

              p.x = x1;
              p.y = y1;
              p.setStyle({
                opacity: p._opacity * (1 - _t)
              });

              vy = vy + ay * dt;
              t0 = _t;
            })
            .done(function () {
              that.zr.remove(particle);
            })
            .start();
        })();
      }
    }
  },
}
</script>

<style>
.example-container {
  width: 100%;
  height: 100%;
  margin: auto;
}
</style>
