<template>
  <div class="container">
    <el-row class="first" type="flex" justify="space-between">
      <!-- 标志图片区 -->
      <div class="logoPart">
        丰融保险保函
      </div>

      <!-- nav菜单栏 -->
      <el-row type="flex" class="navs">
        <!-- <nuxt-link v-for="(item, index) in navs" :key="index" :to="item.links">{{ item.name }}</nuxt-link> -->
        <ul style="display: flex">
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
      lists: ['哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈哈']
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
  // width:1920px;
  height: 140px;
  background: rgba(255, 255, 255, 1);
  // margin: 0 241px;
  .first {
    height: 76px;
    line-height: 76px;
    // margin: 0 auto;

    .navs {
      flex: 1;
      font-size: 24px;
      justify-content: space-around;
      // border-bottom: 1px solid #000;
      li {
        // border: 1px solid #000;
        :hover {
          // border-bottom: 1px solid #000;
        }
      }
    }
    .logoPart {
      width: 204px;
      height: 32px;
      font-size: 34px;
      font-family: Tensentype MingSongJ-W8;
      font-weight: 800;
      color: rgba(52, 52, 52, 1);
      line-height: 50px;
    }
    .el-avatar {
      // vertical-align: unset;
      vertical-align: middle;
    }
  }

  .scrollContainer {
    /* color: red; */
    font-size: 18px;
    // margin-left: 10px;
    width: 1102px;
    margin: 0 auto;
    height: 18px;
    // border: 1px solid #000;
    line-height: 18px;
    // overflow: hidden;
  }
}
</style>
