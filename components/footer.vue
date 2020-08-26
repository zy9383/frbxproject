<template>
  <div class="footer">
    <div class="main">
      <el-row type="flex">
        <el-col>
          <p>
            <a style="fontSize: 20px !important; fontWeight: bold !important" href="#">产品中心</a>
          </p>
          <p>
            <a href="#">工程投标保函</a>
          </p>
          <p>
            <a href="#">合同履约保函</a>
          </p>
          <p>
            <a href="#">工资支付保函</a>
          </p>
          <p>
            <a href="#">工程质量保函</a>
          </p>
        </el-col>
        <el-col>
          <p>
            <a style="fontSize: 20px !important; fontWeight: bold !important" href="#">新闻中心</a>
          </p>
          <p>
            <a href="#">招标公告</a>
          </p>
          <p>
            <a href="#">政策法规</a>
          </p>
          <p>
            <a href="#">新闻资讯</a>
          </p>
          <p>
            <a href="#">平台公告</a>
          </p>
        </el-col>
        <el-col>
          <p>
            <a style="fontSize: 20px !important; fontWeight: bold !important" href="#">关于我们</a>
          </p>
          <p>
            <a href="#">公司介绍</a>
          </p>
          <p>
            <a href="#">联系我们</a>
          </p>
          <p>
            <a href="#">招贤纳士</a>
          </p>
        </el-col>
        <el-col>
          <p>
            <a style="fontSize: 20px !important; fontWeight: bold !important" href="#">帮助中心</a>
          </p>
          <p>
            <a href="#">购买/退保指南</a>
          </p>
          <p>
            <a href="#">投保资料</a>
          </p>
          <p>
            <a href="#">申请理赔</a>
          </p>
          <p>
            <a href="#">常见问题</a>
          </p>
        </el-col>
        <el-col class="last">
          <p>服务热线</p>
          <h3>010-68368808</h3>
        </el-col>
      </el-row>
      <div class="line"></div>
      <div class="banquan">
        <p
          style="fontSize: 14px; fontWeight: 400"
        >版权所有©建设工程信息服务平台 CopyRight© All Rights Reserved 京ICP备11004160号-3</p>
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
  background-color: #2c2d2d;
  color: #ffffff;
  // background-color: #333;
  .main {
    width: 1200px;
    margin: 0 auto;
    padding-bottom: 20px;
    .el-row {
      // border-bottom: 1px solid #FFFFFF;
      padding: 40px 0;
      .el-col {
        // margin: 40px 0;
        font-size: 14px;
        letter-spacing: 2px;
        line-height: 20px;
        font-weight: 400;
        margin-top: 14px;
        :first-child {
          font-size: 18px;
          font-weight: bold;
          margin-bottom: 20px;
        }
        a {
          color: #FFFFFF;
          font-size: 16px !important;
          font-weight: 400 !important;
        }
        p {
          margin-bottom: 10px;
        }
      }
      .last {
        text-align: right;
      }
    }
    .line {
      // width:1440px;
      height: 1px;
      background: rgba(255, 255, 255, 1);
      opacity: 0.14;
    }
    .banquan {
      margin-top: 29px;
      text-align: center;
    }
  }
}
</style>
