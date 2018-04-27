<template>
  <div id="start">
    <p>林惠蘭 | 種子盆栽</p>
    <h1>你適合什麼樣的種子？haha</h1>
    <div class="start-btn" @click="showExam">點我開始測驗！</div>
  </div>
</template>

<script>
export default {
  name: 'start',
  data () {
    return {
    }
  },
  methods: {
    showExam: function () {
      this.$parent.isExam = true
    },
    scrollto: function (p) {
      var y = 0
      var ct = 0
      var fn = function () {
        ct += 1 / 60
        var pos = ct / 5
        var t = (-0.5 * (Math.cos(Math.PI * pos) - 1))
        window.scrollTo(0, y)
        y = y + (p * t)
        if (y < p) {
          setTimeout(fn, 1000 / 60)
        }
      }
      fn()
    }
  }
}
</script>

<style scoped>
  #start{
    width: 100%;
    background-image: linear-gradient(25deg, #56BA60, #9DE563);
    padding: 20px;
    color: #FFF;
  }
  h1 {
    font-size: 3rem;
    margin: 5rem 0;
    line-height: 2rem;
  }
  .start-btn {
    font-size: 1.2rem;
    width: 200px;
    margin: 10px auto;
    padding: 10px;
    border-radius: 100px;
    background-color: rgba(255,255,255,0.5);
    cursor: pointer;
    color: #000;
  }
</style>
