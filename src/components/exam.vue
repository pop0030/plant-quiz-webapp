<template>
  <div id="exam">
    <transition name="exam">
    <div v-if="this.$parent.isExam">
      <div :class="[{'subshow': e.isShow}, {'subend': e.isAns}]" class="subject" v-for="(e, i) in exams" v-bind:key="e">
        <div class="topic" v-text="e.topic"></div>
        <ul class="option-list">
          <li v-for="(a, n) in e.options" v-text="a.string" @click="choice(i, a.value)"></li>
        </ul>
      </div>
    </div>
    </transition>
  </div>
</template>

<script>
import exam from '../assets/exam'

function genExamArray (array) {
  var resArray = []
  var i, j, t
  for (i = 0; i < array.length; i++) {
    array[i].isAns = false
    array[i].isShow = false
    j = Math.floor(Math.random() * (i + 1))
    t = array[i]
    array[i] = array[j]
    array[j] = t
  }
  array[0].isShow = true
  resArray = array
  return resArray
}

export default {
  name: 'exam',
  data () {
    return {
      exams: genExamArray(exam.arry)
    }
  },
  methods: {
    choice: function (indexOfTopic, value) {
      var topic = this.exams[indexOfTopic]
      topic.isAns = true
      topic.isShow = false
      var next = this.exams[indexOfTopic + 1]
      this.$parent.score += value
      if (next) {
        next.isShow = true
      } else {
        this.$parent.isResult = true
      }
    }
  }
}
</script>

<style scoped>
  #exam{
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }
  #exam>div{
    position: relative;
  }
  .exam-enter{
    opacity: 0;
  }
  .exam-enter-active{
    transition: opacity 1s;
  }
  .subject{
    text-align: left;
    padding: 30px;
    width: 50%;
    margin: 30px auto;
    box-shadow: 0px 3px 15px -1px rgba(0,0,0,0.3);
    border-radius: 5px;
    position: absolute;
    left: 20%;
    opacity: 0;
    transition: all 1s;
  }
  .subshow{
    opacity: 1;
    z-index: 1;
    left: 25%;
    transition: all 1s;
  }
  .subend{
    left: 30%;
  }
  .topic{
    font-size: 1.2rem;
  }
  .option-list{
    cursor: pointer;
    list-style: none;
    padding: 30px 10px 10px 10px;
  }
  .option-list>li{
    color: #000;
    padding: 8px;
    margin-bottom: 5px;
    opacity: 0.75;
  }
  .option-list>li:hover{
    opacity: 1;
  }
</style>