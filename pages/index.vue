<template>
  <div class="container">
    <!-- 轮播图部分 -->
    <div class="first">
      <!-- trigger 指示器触发方式 -->
      <!-- interval 自动切换的时间间隔 -->
      <el-carousel trigger="click" :interval="time">
        <el-carousel-item v-for="(item, index) in banners" :key="index">
          <img :src="item.banner_url" alt />
        </el-carousel-item>
      </el-carousel>
    </div>

    <!-- 申请保函流程部分 -->
    <div class="apply">
      <p style="fontSize: 30px">申请保函流程</p>
      <p style="fontSize: 20px">Application process</p>
      <el-row type="flex" style="marginTop: 64px; marginBottom: 100px">
        <el-col>
          <div class="process">
            <i style="fontSize: 60px; color: #326CEB" class="el-icon-edit"></i>
            <span style="fontSize: 30px">登录注册</span>
          </div>
        </el-col>
        <el-col>
          <div class="process">
            <i style="fontSize: 60px; color: #326CEB" class="el-icon-edit"></i>
            <span style="fontSize: 30px">选择产品</span>
          </div>
        </el-col>
        <el-col>
          <div class="process">
            <i style="fontSize: 60px; color: #326CEB" class="el-icon-edit"></i>
            <span style="fontSize: 30px">填写保单</span>
          </div>
        </el-col>
        <el-col>
          <div class="process">
            <i style="fontSize: 60px; color: #326CEB" class="el-icon-edit"></i>
            <span style="fontSize: 30px">完成支付</span>
          </div>
        </el-col>
        <el-col>
          <div class="process">
            <i style="fontSize: 60px; color: #326CEB" class="el-icon-edit"></i>
            <span style="fontSize: 30px">投保成功</span>
          </div>
        </el-col>
      </el-row>
    </div>

    <!-- 产品中心部分 -->
    <div class="product">
      <p style="fontSize: 30px; color: #212121">产品中心</p>
      <p style="fontSize: 20px; color: #666666">Product Center</p>
      <!-- 四个模块 -->
      <div class="center">
        <!-- 单个产品盒子 -->
        <div v-for="item in producttext" :key="item" class="center-box">
          <!-- 图片区域 -->
          <div class="image"></div>
          <p class="text">{{ item }}</p>
          <div style="width: 60px; height: 4px; backgroundColor: #316CEB; margin: 22px auto 0"></div>
          <!-- <el-button>查看详情</el-button> -->
          <div class="check" v-if="details">查看详情</div>
          <div class="detail" v-else>履约保函是指：应劳务方和承包方（申请人）的请求，银行金融机构向工程的业主方（受益人）做出的一种履约保证承诺。如果劳务方和承包方日后未能按时、按质、按量完成其所承建的工程，则银行将向业主方···一笔约占合约金额5%~10%的款项。</div>
        </div>
      </div>
    </div>

    <!-- 新闻中心部分 -->
    <div class="news">
      <p style="fontSize: 30px; color: #212121">新闻中心</p>
      <p style="fontSize: 20px; color: #666666">News Center</p>
      <div class="newsbox">
        内容
      </div>
    </div>

    <!-- 合作伙伴部分 -->
    <div class="partner">
      <p style="fontSize: 30px; color: #212121">合作伙伴 </p>
      <p style="fontSize: 20px; color: #666666">cooperative partner</p>
      <!-- 合作伙伴内容区 -->
      <div class="partner-content">
        <!-- 单个合作伙伴 -->
        <div class="contentbox">中国太平</div>
        <div class="contentbox">中国太平</div>
        <div class="contentbox">中国太平</div>
        <div class="contentbox">中国太平</div>
        <div class="contentbox">中国太平</div>
        <div class="contentbox">中国太平</div>
      </div>
    </div>

    <div class="bottom">
      <div class="bottombox">申请速度快</div>
      <div class="bottombox">申请速度快</div>
      <div class="bottombox">申请速度快</div>
      <div class="bottombox">申请速度快</div>
    </div>
  </div>
</template>

<script>
// import Scroller from '@/components/scroll.vue'
export default {
  // components: {
  //   Scroller
  // },
  data () {
    return {
      banners: [],
      time: 5000,
      producttext: ['工程投保保证保险保函', '合同履约保证保险保函', '工资支付保证保险保函', '工程质量保证保险保函'],
      details: true
    }
  },
  mounted () {
    this.$axios({
      method: 'post',
      url: 'index/banner'
    }).then((res) => {
      const { data } = res.data
      this.banners = data
    })
  }
}
</script>

<style lang="less" scoped>
.container {
  .first {
    background-color: #eee;
    padding-top: 15px;
    .el-carousel {
      height: 480px;
      // background-color: #eee;
      margin-top: 10px;
    }
  }

  .apply {
    margin-top: 100px;
    // background-color: #ccc;
    text-align: center;
    .process {
      // width:244px;
      height: 160px;
      line-height: 160px;
      border: 2px solid #BDBDBD;
    }
  }
  // 产品中心
  .product {
    padding: 100px 0 67px 0;
    background-color: #F5F6F8;
    text-align: center;
    .center {
      display: flex;
      margin-top: 44px;
      .center-box {
        cursor: pointer;
        padding-top: 20px;
        width: 360px;
        height: 570px;
        .image {
          width: 320px;
          height: 342px;
          margin: 0 20px 20px;
          border: 1px solid #000;
        }
        .text {
          font-size: 24px;
        }
        .check {
          width: 140px;
          height: 40px;
          line-height: 40px;
          border: 1px solid #316CEB;
          border-radius: 20px;
          margin: 58px auto 0;
        }
        .detail {
          width:360px;
          height:116px;
          padding: 13px;
          font-size: 14px;
          background:rgba(49,108,235,1);
        }
      }
      :hover {
        background:rgba(255,255,255,1);
      }
    }
  }
  // 新闻中心
  .news {
    text-align: center;
    // background-color: #ccc;
    padding: 100px 0;
    .newsbox {
      // width:1100px;
      height:904px;
      margin: 64px auto 0;
      background:rgba(255,255,255,1);
      box-shadow:0px 0px 49px 0px rgba(139,139,139,0.16);
      border-radius:10px;
    }
  }
  // 合作伙伴
  .partner {
    // width:1920px;
    height:740px;
    text-align: center;
    padding: 100px 0;
    background:rgba(245,246,248,1);
    .partner-content {
      display: flex;
      flex-wrap: wrap;
      margin-top: 64px;
      .contentbox {
        width:280px;
        height:180px;
        margin-bottom: 10px;
        line-height: 180px;
        background:rgba(255,255,255,1);
      }
    }
  }

  .bottom {
    height: 277px;
    display: flex;
    justify-content: space-between;
    .bottombox {
      height: 77px;
      width: 240px;
      margin-top: 100px;
      border: 1px solid #000;
      line-height: 77px;
    }
  }
}
</style>
