<template>
  <div class="product">
    <!-- 头部图片、导航区域 -->
    <div class="top">
      <!-- 图片展示区域 -->
      <div class="img"></div>
      <!-- 导航区域 -->
      <div class="navigation">
        <i class="el-icon-location"></i>
        <span>当前位置：产品中心</span>
      </div>
    </div>
    <!-- 内容区域 -->
    <div class="content">
      <!-- 第一行Tab切换 -->
      <div class="tabs">
        <!-- 标签 -->
        <a v-for="(item, index) in tabs" :key="index" href="javascript:void(0)" @click="tabChange(index + 1)">{{item}}</a>
        <!-- <a href="javascript:void(0)" @click="tabChange(child2)">第二项</a>
        <a href="javascript:void(0)" @click="tabChange(child3)">第三项</a>
        <a href="javascript:void(0)" @click="tabChange(child4)">第四项</a> -->
      </div>
      <!-- 第二行切换Tab的内容区 -->
      <!-- 动态地绑定到它的 is 特性，让多个组件可以使用同一个挂载点，并动态切换。 -->
      <div class="tabs-content" :is="currentView"></div>
    </div>
  </div>
</template>

<script>
// 导入子组件
import child1 from '@/components/product/child1'
import child2 from '@/components/product/child2'
import child3 from '@/components/product/child3'
import child4 from '@/components/product/child4'
export default {
  data () {
    return {
      child1: 'child1',
      child2: 'child2',
      child3: 'child3',
      child4: 'child4',
      currentView: 'child1', // 默认选中第一项
      tabs: ['工程投标保证保险保函', '合同履约保证保险保函', '工资支付保证保险保函', '工程质量保证保险保函']
    }
  },
  methods: {
    tabChange (tabItem) {
      this.currentView = 'child' + tabItem
    }
  },
  components: {
    child1,
    child2,
    child3,
    child4
  }
}
</script>

<style lang="less" scoped>
.product {
  .top {
    .img {
      height: 180px;
      background-color: #ccc;
    }
    .navigation {
      // display: flex;
      width: 1200px;
      height: 48px;
      line-height: 48px;
      margin: 0 auto;
      font-size: 16px;
      background: rgba(255, 255, 255, 1);
      .el-icon-location {
        font-size: 18px;
        color: #326ceb;
      }
    }
  }
  .content {
    background-color: #f6f7f8;
    // margin-bottom: 35px;
    .tabs {
      display: flex;
      justify-content: space-between;
      width: 1200px;
      height: 118px;
      margin: 0 auto;
      padding: 35px 0;
      font-size: 20px;
      a {
        width:260px;
        height:48px;
        line-height: 48px;
        text-align: center;
        background:#FFFFFF;
        border-radius:4px;
      }
    }
  }
}
</style>
