<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div>新增一串文字内容</div>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>
<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  created() {
    console.log('66666666666666')
  }
}
</script>
