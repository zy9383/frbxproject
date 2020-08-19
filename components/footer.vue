<template>
  <div class="footer">
    <div class="main">
      <el-row type="flex">
        <el-col>
          <p>产品中心</p>
          <p>工程投标保函</p>
          <p>合同履约保函</p>
          <p>工资支付保函</p>
          <p>工程质量保函</p>
        </el-col>
        <el-col>
          <p>新闻中心</p>
          <p>招标公告</p>
          <p>政策法规</p>
          <p>新闻资讯</p>
          <p>平台公告</p>
        </el-col>
        <el-col>
          <p>关于我们</p>
          <p>公司介绍</p>
          <p>联系我们</p>
          <p>招贤纳士</p>
        </el-col>
        <el-col>
          <p>帮助中心</p>
          <p>购买/退保指南</p>
          <p>投保资料</p>
          <p>申请理赔</p>
          <p>常见问题</p>
        </el-col>
        <el-col class="last">
          <p>服务热线</p>
          <h3>010-68368808</h3>
        </el-col>
      </el-row>
      <div class="line"></div>
      <div class="banquan">
        <p style="fontSize: 14px; fontWeight: 400">版权所有©建设工程信息服务平台 CopyRight© All Rights Reserved 京ICP备11004160号-3</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="less" scoped>
.footer {
    height: 340px;
    // border: 1px solid #000;
    background-color: #2C2D2D;
    color: #FFFFFF;
  // background-color: #333;
    .main {
    margin: 0 40px;
    padding-bottom: 20px;
    .el-row {
      // border-bottom: 1px solid #FFFFFF;
      .el-col {
        margin: 40px 0;
        font-size: 16px;
        font-weight: 400;
        :first-child {
          font-size: 20px;
          font-weight: bold;
          margin-bottom: 20px;
        }
        h3 {
          margin-bottom: 10px;
        }
      }
      .last {
        text-align: right;
      }
    }
    .line {
      // width:1440px;
      height:1px;
      background:rgba(255,255,255,1);
      opacity:0.14;
    }
    .banquan {
      margin-top: 20px;
      text-align: center;
    }
  }
}
</style>
