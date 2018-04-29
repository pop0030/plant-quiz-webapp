<template>
  <div id="result">
    <div v-if="this.$parent.isResult" class="result-card">
      <h1>測驗結果</h1>
      <img src="../assets/img/001.jpg" alt="">
      <div class="right">
        <h2>{{ seeds[this.$parent.score-1].name }}</h2>
        <p>被遺忘的小種子，被拾起的大發現。傾聽林惠蘭老師圖文解說。種子要告訴你的生活大小事。種子、季節、風水、生活、美食。看林惠蘭老師教你如何用種子的成長體會人生，用盆栽的灌溉滋養生活。</p>
        <div class="buttom">
          <a href="">重新開始</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import seeds from '../assets/seeds'
export default {
  name: 'result',
  data () {
    return {
      seeds: seeds.arry
    }
  }
}
</script>

<style scoped>
#result{
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
}
@keyframes result {
  0% {opacity: 0}
  100% {opacity: 1}
}
.result-card{
  margin: 30px auto;
  width: 60%;
  text-align: left;
  animation: result 1s 1s both;
}
.result-card>h1{
  text-align: center;
  margin-bottom: 30px;
  font-weight: 100;
  font-size: 1.4rem;
}
.right{
  float: right;
  width: 70%;
  padding: 0 20px;
  position: relative;
}
.buttom{
  position: absolute;
  right: 0;
  top: 250px;
  text-align: right;
}
.buttom>a{
  display: inline-block;
  text-align: center;
  background-color: #008EF3;
  color: #FFF;
  padding: 5px 15px;
  border-radius: 30px;
  margin-left: 10px;
  text-decoration: none;
  font-size: 1.2rem;
  font-weight: bold;
}
img{
  width: 30%;
  float: left;
}
h2{
  font-size: 2rem;
  text-align: left;
}
.right>p{
  font-size: 1rem;
  margin-top: 20px;
}
</style>