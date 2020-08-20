<template>
  <div>
    <Header />
    <Nuxt />
    <Footer />
  </div>
</template>

<script>
import Header from '@/components/header'
import Footer from '@/components/footer'
export default {
  components: {
    Header,
    Footer
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
