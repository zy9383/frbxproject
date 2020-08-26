<template>
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
            <p style="fontSize: 16px; fontWeight: 400; color: #666666; lineHeight: 36px">{{item.title2}}</p>
            <div class="btn">查看购买</div>
          </div>
        </el-col>
      </el-row>
    </div>
    <a href="#" style="color: #326CEB; fontSize: 18px; lineHeight: 70px">查看更多&gt;&gt;</a>
  </div>
</template>

<script>
export default {
  data () {
    return {
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
      }]
    }
  }
}
</script>

<style lang="less" scoped>
.box {
  // height: 100%;
  margin: 20px 30px 0 30px;
  // background-color: #ccc;
  .one {
    height: 178px;
    padding-top: 30px;
    border-bottom: 1px solid #DCDCDC;
    .left {
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      width:90px;
      height:110px;
      background:rgba(50,108,235,1);
    }
    .right {
      margin-left: 20px;
      text-align: left;
      // background-color: pink;
      .btn {
        width:140px;
        height:40px;
        margin-top: 15px;
        font-size: 18px;
        color: #326CEB;
        line-height: 40px;
        text-align: center;
        border:1px solid rgba(50,108,235,1);
        border-radius:20px;
      }
    }
  }
}
</style>
