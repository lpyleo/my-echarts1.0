<template>
  <div id="app">
    <MyEcharts :options="options"></MyEcharts>
  </div>
</template>

<script>
import MyEcharts from './components/MyEcharts.vue'
import options from './options'

export default {
  name: 'App',
  components: {
    MyEcharts
  },
  data() {
    return {
      options
    }
  }
}
</script>