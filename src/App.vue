<template>
  <div id="app">
    <start></start>
    <div class="content">
      <exam></exam>
      <result></result>
    </div>
  </div>
</template>

<script>
import start from './components/start'
import exam from './components/exam'
import result from './components/result'

export default {
  name: 'app',
  data () {
    return {
      score: 1,
      isExam: false,
      isResult: false
    }
  },
  components: {
    start,
    exam,
    result
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html,body {
  width: 100%;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;
}
.content {
  position: relative;
}
</style>
