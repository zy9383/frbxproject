<template>
  <div class="container">
    <!-- 上部分简介区域 -->
    <el-row class="top">
      <el-col span="4">
        <div class="left"></div>
      </el-col>
      <el-col>
        <div class="first">工程投标保证保险保函</div>
        <div
          class="second"
        >建设工程投标保证保险保函是指：在招标投标中招标人为保证投标人不得撤销投标文件、中标后不得无正当理由不与招标人订立合同等，要求投标人在提交投标文件时一并提交的一般由银行出具的书面担保。</div>
        <div class="tabbtns">
          <div class="tabbtn1">全面认可</div>
          <div class="tabbtn2">与保证金、银行保函等效</div>
          <div class="tabbtn3">线上投保</div>
          <div class="tabbtn4">即刻出单</div>
          <div class="tabbtn5">即刻生效</div>
          <div class="tabbtn6">电子保单保函</div>
          <div class="tabbtn7">诚信一体化平台核验</div>
        </div>
      </el-col>
    </el-row>
    <!-- 下半部分内容区域 -->
    <div class="content">
      <!-- 搜索框部分 -->
      <div class="content-first">
        <el-input placeholder="请输入关键字" v-model="input3" class="input-with-select">
          <el-button
            style="backgroundColor: #316CEB; color: #FFFFFF; fontSize: 18px"
            slot="append"
          >搜索</el-button>
        </el-input>
        <el-button style="backgroundColor: #316CEB; fontSize: 18px" type="primary">手动填写项目</el-button>
      </div>
      <!-- 城市部分 -->
      <el-row style="marginBottom: 30px; cursor: pointer" type="flex">
        <el-col span="2">服务范围：</el-col>
        <el-col>
          <span style="marginRight: 40px" v-for="(item, index) in provinces" :key="index">{{ item }}</span>
        </el-col>
      </el-row>
      <!-- 地区部分 -->
      <el-row style="marginBottom: 30px; cursor: pointer" type="flex">
        <el-col span="2">城市：</el-col>
        <el-col>
          <span style="marginRight: 45px" v-for="(item, index) in cities" :key="index">{{ item }}</span>
        </el-col>
      </el-row>
      <!-- 地区下面内容部分 -->
      <div class="box">
        <!-- 单个盒子 -->
        <div class="one" v-for="(item, index) in rights" :key="index">
          <el-row type="flex">
            <el-col class="left">
              <!-- 左侧日期蓝标部分 -->
              <p style="fontSize: 22px; fontWeight: bold; color: #FFFFFF">{{item.datas}}</p>
              <div style="width: 24px; height: 3px; background: #FFFFFF; margin: 0 auto"></div>
              <p style="fontSize: 16px; color: #FFFFFF">{{item.years}}</p>
            </el-col>
            <el-col>
              <!-- 右侧文字内容部分 -->
              <div class="right">
                <p style="fontSize: 20px; fontWeight: bold; color: #343434">{{item.title}}</p>
                <p
                  style="fontSize: 16px; fontWeight: 400; color: #666666; lineHeight: 36px"
                >{{item.title2}}</p>
                <div class="btn" @click="shopBtn">查看购买</div>
              </div>
            </el-col>
          </el-row>
        </div>
        <!-- <a href="#" style="color: #326CEB; fontSize: 18px; lineHeight: 70px">查看更多&gt;&gt;</a>
        -->
        <!-- 分页部分 -->
        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="currentPage4"
          :page-sizes="[100, 200, 300, 400]"
          :page-size="100"
          layout="total, prev, pager, next, jumper"
          :total="400"
        ></el-pagination>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      provinces: ['上海市', '江苏省', '浙江省', '安徽省', '福建省', '江西省', '山东省'],
      cities: ['合肥市', '芜湖市', '蚌埠市', '淮南市', '马鞍山市', '淮北市', '铜陵市', '安庆市', '黄山市', '滁州市', '阜阳市', '宿州市', '六安市', '亳州市', '宣城市'],
      // 右侧文字内容部分
      rights: [{
        datas: '05-21',
        years: '2020',
        title: '泗县界牌张村张陶安置小区农民文化广场工程采购项目',
        title2: 'SXCG2020332  泗县界牌张村张陶安置小区农民文化广场工程采购项目'
      }, {
        datas: '05-19',
        years: '2020',
        title: '灵璧县迎宾大道（凤河-汴河路段）奇石大道（滨河路-凌山路段）汴河路（迎宾大道...',
        title2: 'LBGC2020091  灵璧县迎宾大道（凤河-汴河路段）奇石大道（滨河路-凌山路段）汴河路（迎宾大道-薄山路...'
      }, {
        datas: '05-12',
        years: '2020',
        title: '宿州市埇桥区31个美丽乡村污水处理（厂）站及配套管网提升改造项目工程总承包(EP...',
        title2: 'YQGC2020162   宿州市埇桥区31个美丽乡村污水处理（厂）站及配套管网提升改造项目工程总承包（EPC）...'
      }, {
        datas: '05-21',
        years: '2020',
        title: '泗县界牌张村张陶安置小区农民文化广场工程采购项目',
        title2: 'SXCG2020332  泗县界牌张村张陶安置小区农民文化广场工程采购项目'
      }, {
        datas: '05-19',
        years: '2020',
        title: '灵璧县迎宾大道（凤河-汴河路段）奇石大道（滨河路-凌山路段）汴河路（迎宾大道...',
        title2: 'LBGC2020091  灵璧县迎宾大道（凤河-汴河路段）奇石大道（滨河路-凌山路段）汴河路（迎宾大道-薄山路...'
      }, {
        datas: '05-12',
        years: '2020',
        title: '宿州市埇桥区31个美丽乡村污水处理（厂）站及配套管网提升改造项目工程总承包(EP...',
        title2: 'YQGC2020162   宿州市埇桥区31个美丽乡村污水处理（厂）站及配套管网提升改造项目工程总承包（EPC）...'
      }]
    }
  },
  methods: {
    shopBtn () {
      this.$router.push('/product/productdetail')
    }
  }
}
</script>

<style lang="less" scoped>
.container {
  width: 1200px;
  height: 1650px;
  margin: 0 auto;
  background: rgba(255, 255, 255, 1);
  border-radius: 10px;
  .top {
    display: flex;
    padding: 40px 0;
    margin: 0 30px;
    border-bottom: 1px solid #dcdcdc;
    .left {
      width: 137px;
      height: 146px;
      background-color: #ccc;
    }
    .first {
      font-size: 24px;
      font-family: PingFang SC;
      font-weight: 500;
      color: #343434;
      // background-color: #ccc;
      line-height: 50px;
    }
    .second {
      margin-bottom: 14px;
      font-size: 16px;
      color: #666666;
      font-weight: 400;
    }
    .tabbtns {
      display: flex;
      .tabbtn1 {
        // width:72px;
        height: 24px;
        font-size: 14px;
        color: #2e74c2;
        border: 1px solid rgba(46, 116, 194, 1);
        border-radius: 4px;
        margin-right: 12px;
        padding: 0 9px;
      }
      .tabbtn2 {
        height: 24px;
        font-size: 14px;
        color: #65b560;
        border: 1px solid #65b560;
        border-radius: 4px;
        margin-right: 12px;
        padding: 0 9px;
      }
      .tabbtn3 {
        height: 24px;
        font-size: 14px;
        color: #f07f31;
        border: 1px solid #f07f31;
        border-radius: 4px;
        margin-right: 12px;
        padding: 0 9px;
      }
      .tabbtn4 {
        height: 24px;
        font-size: 14px;
        color: #e66058;
        border: 1px solid #e66058;
        border-radius: 4px;
        margin-right: 12px;
        padding: 0 9px;
      }
      .tabbtn5 {
        height: 24px;
        font-size: 14px;
        color: #b893dc;
        border: 1px solid #b893dc;
        border-radius: 4px;
        margin-right: 12px;
        padding: 0 9px;
      }
      .tabbtn6 {
        height: 24px;
        font-size: 14px;
        color: #5fb0e4;
        border: 1px solid #5fb0e4;
        border-radius: 4px;
        margin-right: 12px;
        padding: 0 9px;
      }
      .tabbtn7 {
        height: 24px;
        font-size: 14px;
        color: #00899f;
        border: 1px solid #00899f;
        border-radius: 4px;
        padding: 0 9px;
      }
    }
  }
  .content {
    margin: 30px;
    // background-color: #ccc;
    .content-first {
      text-align: center;
      .input-with-select {
        width: 360px;
        margin-right: 80px;
        margin-bottom: 30px;
      }
    }
    .box {
      // height: 100%;
      margin: 20px 30px 0 30px;
      text-align: center;
      // background-color: #ccc;
      .one {
        height: 178px;
        padding-top: 30px;
        border-bottom: 1px solid #dcdcdc;
        .left {
          display: flex;
          flex-direction: column;
          justify-content: space-evenly;
          width: 90px;
          height: 110px;
          background: rgba(50, 108, 235, 1);
        }
        .right {
          margin-left: 20px;
          text-align: left;
          // background-color: pink;
          .btn {
            cursor: pointer;
            width: 140px;
            height: 40px;
            margin-top: 15px;
            font-size: 18px;
            color: #326ceb;
            line-height: 40px;
            text-align: center;
            border: 1px solid rgba(50, 108, 235, 1);
            border-radius: 20px;
          }
        }
      }
    }
    .el-pagination {
      padding-top: 40px;
    }
  }
}
</style>
