<template>
  <div class="container">
    <!-- 轮播图部分 -->
    <div class="first">
      <!-- trigger 指示器触发方式 -->
      <!-- interval 自动切换的时间间隔 -->
      <el-carousel height="480px" trigger="click" :interval="time">
        <el-carousel-item v-for="(item, index) in 4" :key="index">
          <!-- <img :src="item.banner_url" alt /> -->
          <!-- <img src="../assets/images/lb1.png" alt /> -->
          <div class="img"></div>
        </el-carousel-item>
      </el-carousel>
    </div>

    <!-- 申请保函流程部分 -->
    <div class="apply">
      <div class="apply-content">
        <p style="fontSize: 30px; color: #212121">申请保函流程</p>
        <p style="fontSize: 14px; color: #666666">Application process</p>
        <el-row type="flex" style="marginTop: 40px; marginBottom: 100px">
          <el-col>
            <div class="process">
              <i style="fontSize: 45px; color: #326CEB" class="el-icon-edit"></i>
              <span style="fontSize: 24px; fontWeight: 400">登录注册</span>
            </div>
          </el-col>
          <el-col>
            <div class="process">
              <i style="fontSize: 45px; color: #326CEB" class="el-icon-edit"></i>
              <span style="fontSize: 24px; fontWeight: 400">选择产品</span>
            </div>
          </el-col>
          <el-col>
            <div class="process">
              <i style="fontSize: 45px; color: #326CEB" class="el-icon-edit"></i>
              <span style="fontSize: 24px; fontWeight: 400">填写保单</span>
            </div>
          </el-col>
          <el-col>
            <div class="process">
              <i style="fontSize: 45px; color: #326CEB" class="el-icon-edit"></i>
              <span style="fontSize: 24px; fontWeight: 400">完成支付</span>
            </div>
          </el-col>
          <el-col>
            <div class="process">
              <i style="fontSize: 45px; color: #326CEB" class="el-icon-edit"></i>
              <span style="fontSize: 24px; fontWeight: 400">投保成功</span>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>

    <!-- 产品中心部分 -->
    <div class="product">
      <div class="product-content">
        <p style="fontSize: 30px; color: #212121">产品中心</p>
        <p style="fontSize: 14px; color: #666666">Product Center</p>
        <!-- 四个模块 -->
        <div class="center">
          <!-- 单个产品盒子 -->
          <div v-for="item in producttext" :key="item" class="center-box" @click="centerboxbtn">
            <!-- 图片区域 -->
            <!-- <div class="image" :style="`background: url(${item.img}}) center center no-repeat; background-size: contain contain`"></div> -->
            <div class="image">
              <img src="../assets/images/img1.png" alt="">
            </div>
            <p class="text">{{ item.text }}</p>
            <div style="width: 60px; height: 4px; backgroundColor: #316CEB; margin: 22px auto 20px"></div>
            <!-- <el-button>查看详情</el-button> -->
            <!-- 查看详情部分 -->
            <div class="check">
              <div class="check-btn">查看详情</div>
            </div>
            <!-- <div class="check">
              <el-button>查看详情</el-button>
            </div> -->
            <!-- <div class="check"> -->
              <!-- <div>查看详情</div> -->
              <!-- <div
                class="detail"
              >履约保函是指：应劳务方和承包方（申请人）的请求，银行金融机构向工程的业主方（受益人）做出的一种履约保证承诺。如果劳务方和承包方日后未能按时、按质、按量完成其所承建的工程，则银行将向业主方···一笔约占合约金额5%~10%的款项。</div> -->
            <!-- </div> -->
            </div>
        </div>
      </div>
    </div>

    <!-- 新闻中心部分 -->
    <div class="news">
      <div class="news-content">
        <p style="fontSize: 30px; color: #212121">新闻中心</p>
        <p style="fontSize: 14px; color: #666666">News Center</p>
        <div class="newsbox">
          <!-- 第一行Tab切换 -->
          <div class="tabs">
            <!-- 标签 -->
            <a v-for="(item, index) in newstabs" :key="index" href="javascript:void(0)" @click="tabChange(index + 1)">{{item}}</a>
          </div>
          <!-- 第二行切换Tab的内容区 -->
          <!-- 动态地绑定到它的 is 特性，让多个组件可以使用同一个挂载点，并动态切换。 -->
          <!-- <div class="tabs-content" :is="currentView"></div> -->
          <div class="tabs-content" :is="currentView"></div>
        </div>
      </div>
    </div>

    <!-- 合作伙伴部分 -->
    <div class="partner">
      <div class="partner-content">
        <p style="fontSize: 30px; color: #212121">合作伙伴</p>
        <p style="fontSize: 20px; color: #666666">cooperative partner</p>
        <!-- 合作伙伴内容区 -->
        <div class="partner-detail">
          <!-- 单个合作伙伴 -->
          <div class="contentbox">
            <img src="../assets/images/hz1.png" alt="">
          </div>
          <div class="contentbox">
            <img src="../assets/images/hz2.png" alt="">
          </div>
          <div class="contentbox">
            <img src="../assets/images/hz3.png" alt="">
          </div>
          <div class="contentbox">
            <img src="../assets/images/hz4.png" alt="">
          </div>
          <div class="contentbox">
            <img src="../assets/images/hz5.png" alt="">
          </div>
          <div class="contentbox">
            <img src="../assets/images/hz6.png" alt="">
          </div>
          <!-- <div class="contentbox">中国太平</div>
          <div class="contentbox">中国太平</div>
          <div class="contentbox">中国太平</div>
          <div class="contentbox">中国太平</div>
          <div class="contentbox">中国太平</div> -->
        </div>
      </div>
    </div>

    <!-- 平台优势部分 -->
    <div class="advanture">
      <div class="advanture-content">
        <img src="../assets/images/db1.png" alt="">
        <!-- <div class="bottombox">申请速度快</div>
        <div class="bottombox">申请速度快</div>
        <div class="bottombox">申请速度快</div>
        <div class="bottombox">申请速度快</div> -->
      </div>
    </div>
  </div>
</template>

<script>
// 导入子组件
import child1 from '@/components/news/child1'
import child2 from '@/components/news/child2'
import child3 from '@/components/news/child3'
import child4 from '@/components/news/child4'
export default {
  components: {
    child1,
    child2,
    child3,
    child4
  },
  data () {
    return {
      // banners: [],
      time: 5000,
      // producttext: ['工程投保保证保险保函', '合同履约保证保险保函', '工资支付保证保险保函', '工程质量保证保险保函'],
      producttext: [{
        text: '工程投保保证保险保函',
        img: '../assets/images/img1.png'
      }, {
        text: '合同履约保证保险保函',
        img: '../assets/images/img2.png'
      }, {
        text: '工资支付保证保险保函',
        img: '../assets/images/img3.png'
      }, {
        text: '工程质量保证保险保函',
        img: '../assets/images/img4.png'
      }],
      details: true,
      child1: 'child1',
      child2: 'child2',
      child3: 'child3',
      child4: 'child4',
      currentView: 'child1', // 默认选中第一项
      newstabs: ['招标公告', '政策法规', '新闻资讯', '平台公告']
    }
  },
  methods: {
    centerboxbtn () {
      this.$router.push('/product')
    },
    tabChange (tabItem) {
      this.currentView = 'child' + tabItem
    }
  },
  mounted () {
    // this.$axios({
    //   method: 'post',
    //   url: 'index/banner'
    // }).then((res) => {
    //   const { data } = res.data
    //   this.banners = data
    // })
  }
}
</script>

<style lang="less" scoped>
.container {
  .first {
    background-color: #eee;
    // padding-top: 15px;
    .el-carousel {
      // height: 480px;
      // background-color: #eee;
      margin-top: 10px;
    }
    .img {
      // width: 100%;
      height: 480px;
      background: url(../assets/images/lb1.png) no-repeat;
      background-size: contain;
    }
  }

  .apply {
    // width: 1200px;
    padding: 80px 0;
    // background-color: #ccc;
    text-align: center;
    .apply-content {
      width: 1200px;
      margin: 0 auto;
      .process {
        width: 216px;
        height: 120px;
        line-height: 120px;
        border: 2px solid #bdbdbd;
      }
    }
  }
  // 产品中心
  .product {
    padding: 100px 0 67px 0;
    background-color: #f5f6f8;
    text-align: center;
    .product-content {
      width: 1200px;
      margin: 0 auto;
      .center {
        display: flex;
        margin-top: 44px;
        .center-box {
          cursor: pointer;
          padding-top: 20px;
          width: 300px;
          height: 504px;
          .image {
            width: 260px;
            height: 277px;
            margin: 0 20px 20px;
            border: 1px solid #000;
          }
          .text {
            font-size: 24px;
          }
          .check {
            width:300px;
            height:116px;
            background:#eee;
            .check-btn {
              width: 140px;
              height: 40px;
              line-height: 40px;
              color: #326CEB;
              border: 1px solid #316ceb;
              border-radius: 20px;
              margin: 0 auto;
              // margin: 58px auto 0;
            }
          }
          // .detail {
          //   overflow: hidden;
          //   width: 300px;
          //   height: 116px;
          //   line-height: 20px;
          //   padding: 13px;
          //   font-size: 14px;
          //   margin-top: 20px;
          //   background: rgba(49, 108, 235, 1);
          // }
        }
        .center-box:hover {
          background: rgba(255, 255, 255, 1);
        }
      }
    }
  }
  // 新闻中心
  .news {
    text-align: center;
    // background-color: #ccc;
    padding: 100px 0;
    .news-content {
      width: 1200px;
      margin: 0 auto;
      .newsbox {
        // width:1100px;
        height: 706px;
        margin: 64px auto 0;
        background: rgba(255, 255, 255, 1);
        box-shadow: 0px 0px 49px 0px rgba(139, 139, 139, 0.16);
        border-radius: 10px;
        .tabs {
          display: flex;
          justify-content: space-evenly;
          height: 80px;
          font-size: 24px;
          line-height: 80px;
          a:first-child {
            color: #316CEB;
          }
        }
      }
    }
  }
  // 合作伙伴
  .partner {
    // width:1920px;
    height: 740px;
    text-align: center;
    padding: 100px 0;
    background: rgba(245, 246, 248, 1);
    .partner-content {
      width: 1200px;
      margin: 0 auto;
      .partner-detail {
        display: flex;
        flex-wrap: wrap;
        margin-top: 64px;
        .contentbox {
          width: 280px;
          height: 180px;
          margin-bottom: 26px;
          margin-right: 20px;
          line-height: 180px;
          background: rgba(255, 255, 255, 1);
          img {
            width: 240px;
            margin-top: 20px;
          }
        }
      }
    }
  }

  .advanture {
    height: 186px;
    text-align: center;
    line-height: 186px;
    .advanture-content {
      width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      img {
        width: 1200px;
        margin-top: 20px;
      }
      .bottombox {
        height: 77px;
        width: 240px;
        // margin-top: 100px;
        border: 1px solid #000;
        line-height: 77px;
      }
    }
  }
}
</style>
