<template>
  <div style="width: 1200px; margin: 0 auto">
    <Header v-show="!(path === '/user/login' || path === '/user/register')" />
    <Nuxt />
    <Footer v-show="!(path === '/user/login' || path === '/user/register')" />
  </div>
</template>

<script>
import Header from '@/components/header'
import Footer from '@/components/footer'
export default {
  components: {
    Header,
    Footer
  },
  data () {
    return {
      path: ''
    }
  },
  mounted () {
    this.path = this.$route.path // this.path = 当前页面路由
  },
  watch: {
    // 监测路由变化
    $route (to, from) {
      this.path = to.path // 打开新页面路由
    }
  }
}
</script>

<style>
/* 配置全局样式 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a {
  margin: 0 10px;
  color: #000;
  text-decoration: none;
}

li {
  list-style: none;
}

</style>
