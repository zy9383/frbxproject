<template>
  <div class="container">
    <el-row class="first" type="flex" justify="space-between">
      <!-- 标志图片区 -->
      <div class="logoPart">
        丰融保险保函
      </div>

      <!-- nav菜单栏 -->
      <el-row class="navs">
        <!-- <nuxt-link v-for="(item, index) in navs" :key="index" :to="item.links">{{ item.name }}</nuxt-link> -->
        <ul>
          <li>
            <nuxt-link to="/">首页</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/product">产品中心</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/news">新闻中心</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/about">关于我们</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/help">帮助中心</nuxt-link>
          </li>
        </ul>
      </el-row>

      <!-- 登录 / 注册 -->
      <!-- <el-button style="height: 40px" type="small" v-if="true" @click="userLogin">登录 / 注册</el-button> -->
      <div v-if="true">
        <el-avatar size="small" :src="userImg"></el-avatar>
        <!-- <span>未登录</span> -->
        <nuxt-link to="/user/login">未登录</nuxt-link>
      </div>
      <div v-else>
        <el-avatar size="small" :src="userImg"></el-avatar>
        <span>用户名</span>
      </div>
    </el-row>

    <el-row type="flex">
      <Scroller :lists="lists" class="scrollContainer"></Scroller>
    </el-row>
  </div>
</template>

<script>
import Scroller from '@/components/scroll.vue'
export default {
  components: {
    Scroller
  },
  data () {
    return {
      // navs: [{
      //   links: '/',
      //   name: '首页'
      // }, {
      //   links: '/product',
      //   name: '产品中心'
      // }, {
      //   links: '/news',
      //   name: '新闻中心'
      // }],
      userImg: 'https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png',
      lists: ['丰融保险保函丰融保险保函丰融保险保函丰融保险保函丰融保险保函丰融保险保函丰融保险保函丰融保险保函丰融保险保函丰融保险保函']
    }
  },
  methods: {
    userLogin () {
      this.$router.push('/user/login')
    }
  }
}
</script>

<style lang="less" scoped>
.container {
  width:1200px;
  height: 112px;
  background: rgba(255, 255, 255, 1);
  margin: 0 auto;
  .first {
    height: 64px;
    line-height: 64px;
    // margin: 0 auto;

    .navs {
      // display: flex;
      // flex: 1;
      // justify-content: space-between;
      font-size: 18px;
      .nuxt-link-exact-active {
        // background: #316CEB;
        color: #316CEB !important;
        font-weight: bold;
      }
      ul {
        display: flex;
        // flex: 1;
        justify-content: space-between;
        width: 800px;
        li:hover {
          border-bottom: 4px solid #316CEB;
          border-radius: 2px;
        }
      }
    }
    .logoPart {
      width: 204px;
      height: 32px;
      font-size: 30px;
      font-family: Tensentype MingSongJ-W8;
      font-weight: 800;
      color: rgba(52, 52, 52, 1);
      line-height: 50px;
      margin-top: 8px;
    }
    .el-avatar {
      vertical-align: middle;
    }
  }

  .scrollContainer {
    /* color: red; */
    font-size: 16px;
    // margin-left: 10px;
    width: 1033px;
    margin: 16px auto;
    height: 48px;
    // border: 1px solid #000;
    // line-height: 16px;
    // overflow: hidden;
  }
}
</style>
