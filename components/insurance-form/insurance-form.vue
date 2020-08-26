<template>
  <div class="insurance-form">
    <div class="cardForm">
      <!-- 步骤条 -->
      <el-steps :active="activeIndex - 0" align-center finish-status="success">
        <el-step title="填写投保单"></el-step>
        <el-step title="确认信息"></el-step>
        <el-step title="支付保费"></el-step>
        <el-step title="获取保函"></el-step>
      </el-steps>

      <!-- 表单区域 -->
      <el-tabs class="cardarea" v-model="activeIndex" @tab-click="handleClick">
        <!-- 投保单区域 -->
        <el-tab-pane name="0" v-show="activeIndex == 0 ? true : false">
          <!-- 企业信息 -->
          <el-card class="information">企业信息</el-card>
          <el-form
            class="information-content"
            ref="informationRef"
            :model="informationForm"
            :rules="informationRules"
            label-position="left"
            label-width="160px"
          >
            <el-form-item label="营业执照:">
              <el-upload
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple
                :limit="3"
              >
                <el-button>
                  <i class="el-icon-upload2"></i>
                  上传文件
                </el-button>
                <div slot="tip" class="el-upload__tip">
                  <i class="el-icon-paperclip"></i>
                  营业执照
                </div>
              </el-upload>
            </el-form-item>
            <el-form-item label="企业名称:" prop="name">
              <el-input v-model="informationForm.name"></el-input>
            </el-form-item>
            <el-form-item label="社会统一信用代码:" prop="code">
              <el-input v-model="informationForm.code"></el-input>
            </el-form-item>
            <el-form-item label="法人姓名:" prop="CorporateName">
              <el-input v-model="informationForm.CorporateName"></el-input>
            </el-form-item>
            <el-form-item label="法人身份证证件照:">
              <el-upload
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple
                :limit="3"
              >
                <el-button>
                  <i class="el-icon-upload2"></i>
                  上传文件
                </el-button>
                <div slot="tip" class="el-upload__tip">
                  <i class="el-icon-paperclip"></i>
                  身份证证件照正面&nbsp;&nbsp; 身份证证件照反面
                </div>
              </el-upload>
            </el-form-item>
            <el-form-item label="授权委托书:">
              <el-upload
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple
                :limit="3"
              >
                <el-button>
                  <i class="el-icon-download"></i>
                  下载文件
                </el-button>
                <el-button>
                  <i class="el-icon-upload2"></i>
                  上传文件
                </el-button>
                <p class="xiazai">需要下载授权委托书盖章再回传</p>
              </el-upload>
            </el-form-item>
          </el-form>

          <!-- 项目信息 -->
          <el-card class="sports">项目信息</el-card>
          <el-form
            class="sports-content"
            ref="sportsRef"
            :model="sportsForm"
            :rules="sportsRules"
            label-position="left"
            label-width="200px"
          >
            <el-form-item label="地区:" prop="area">
              <el-input v-model="sportsForm.area"></el-input>
            </el-form-item>
            <el-form-item label="项目类型:" prop="type">
              <el-checkbox-group v-model="sportsForm.type">
                <el-checkbox label="工程建设" name="type"></el-checkbox>
                <el-checkbox label="物资采购" name="type"></el-checkbox>
                <el-checkbox label="其他" name="type"></el-checkbox>
              </el-checkbox-group>
            </el-form-item>
            <el-form-item label="项目(标段)名称:" prop="sportsname">
              <el-input v-model="sportsForm.sportsname"></el-input>
            </el-form-item>
            <el-form-item label="项目(标段)编号:" prop="sportsnumber">
              <el-input v-model="sportsForm.sportsnumber"></el-input>
            </el-form-item>
            <el-form-item label="招标项目预估合同金额:" prop="sportsmoney">
              <el-input class="yugu" v-model="sportsForm.sportsmoney" suffix-icon="el-icon-date"></el-input>
            </el-form-item>
            <el-form-item label="投标截止日:" prop="sportsday">
              <el-input
                v-model="sportsForm.sportsday"
                placeholder="请选择日期"
                suffix-icon="el-icon-date"
              ></el-input>
            </el-form-item>
            <el-form-item label="保证金金额:" prop="plight">
              <el-input v-model="sportsForm.plight"></el-input>
            </el-form-item>
            <el-form-item label="投标有效期:" prop="valid">
              <el-input v-model="sportsForm.valid"></el-input>
            </el-form-item>
            <el-form-item label="招标人:" prop="people">
              <el-input v-model="sportsForm.people"></el-input>
            </el-form-item>
            <el-form-item label="招标人统一社会信用代码:" prop="credit">
              <el-input v-model="sportsForm.credit"></el-input>
              <a href="#" class="xinyongcode">查询查询统一社会信用代码</a>
            </el-form-item>
            <el-form-item label="招标代理机构:" prop="mechanism">
              <el-input v-model="sportsForm.mechanism"></el-input>
            </el-form-item>
            <!-- 按钮区域 -->
            <el-form-item class="button">
              <el-button @click="$emit('goback')">上一页</el-button>
              <el-button type="danger" @click="Reset">重置</el-button>
              <el-button type="primary" @click="next">下一页</el-button>
            </el-form-item>
          </el-form>
        </el-tab-pane>
        <!-- 确认信息 -->
        <el-tab-pane name="1" v-show="activeIndex == 1 ? true : false">
          <el-form
            class="information-content"
            ref="informationRef"
            :model="informationForm"
            :rules="informationRules"
            label-position="left"
            label-width="160px"
          >
            <el-form-item label="营业执照:" prop="photo">
              <div class="paperclip">
                <i class="el-icon-paperclip"></i>
                <span>营业执照</span>
              </div>
            </el-form-item>
            <el-form-item label="企业名称:" prop="name"></el-form-item>
            <el-form-item label="社会统一信用代码:" prop="code"></el-form-item>
            <el-form-item label="法人姓名:" prop="CorporateName"></el-form-item>
            <el-form-item label="法人身份证证件照:" prop="IDPhoto">
              <div class="paperclip">
                <i class="el-icon-paperclip"></i>
                <span>身份证证件照正面&nbsp;&nbsp; 身份证证件照反面</span>
              </div>
            </el-form-item>
            <el-form-item label="授权委托书:" prop="book">
              <el-upload
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                multiple
                :limit="3"
              >
                <p class="xiazai">需要下载授权委托书盖章再回传</p>
              </el-upload>
            </el-form-item>
          </el-form>
          <!-- 项目信息 -->
          <el-card class="sports">项目信息</el-card>
          <el-form
            class="sports-content"
            ref="sportsRef"
            :model="sportsForm"
            :rules="sportsRules"
            label-position="left"
            label-width="200px"
          >
            <el-form-item label="地区:">
              <p>安徽省/宿州市</p>
            </el-form-item>
            <el-form-item label="项目类型:">
              <p>工程建设</p>
            </el-form-item>
            <el-form-item label="项目(标段)名称:" prop="sportsname">
              <p>泗县界牌张村张陶安置小区农民文化广场工程采购项目</p>
            </el-form-item>
            <el-form-item label="项目(标段)编号:" prop="sportsnumber">
              <p>SXCG2020332</p>
            </el-form-item>
            <el-form-item label="招标项目预估合同金额:" prop="sportsmoney">
              <p>100000元</p>
            </el-form-item>
            <el-form-item label="投标截止日:" prop="sportsday">
              <p>2020-05-12 09:00:00</p>
            </el-form-item>
            <el-form-item label="保证金金额:" prop="plight">
              <p>15000元</p>
            </el-form-item>
            <el-form-item label="投标有效期:" prop="valid">
              <p>4天</p>
            </el-form-item>
            <el-form-item label="招标人:" prop="people">
              <p>泗县墩集镇人民政府</p>
            </el-form-item>
            <el-form-item label="招标人统一社会信用代码:" prop="credit">
              <p>11341324003203292D</p>
            </el-form-item>
            <el-form-item label="招标代理机构:" prop="mechanism">
              <p>91310114703275983G</p>
            </el-form-item>
          </el-form>
          <div class="return">
            <el-button type="danger" @click="back">返回修改</el-button>
            <el-button type="primary" @click="adddialog">确认</el-button>
          </div>
        </el-tab-pane>
        <!-- 支付保费 -->
        <el-tab-pane name="2" v-show="activeIndex == 2 ? true : false">
          <span>工程联保工程投标保证保险保函</span>
          <span class="payoff">2020-08-19 14:14:00</span>
          <span>应付保费：200元</span>
          <p class="payoffline"></p>
          <span class="means">可以选择以下支付方式：</span>
          <el-button @click="next" class="sure">确定</el-button>
        </el-tab-pane>
        <el-tab-pane name="3">
          <div class="success"></div>
          <p>支付成功</p>
          <div class="orderDetails">
            <el-button type="primary" @click="first" class="homepage">返回首页</el-button>
            <el-button>订单详情</el-button>
          </div>
        </el-tab-pane>
      </el-tabs>

      <!-- 已成功提交保单弹出层 -->
      <el-dialog :visible.sync="centerDialogVisible" center :show-close="false">
        <div class="dialogbox">
          <span class="dialogmoney">
            <i class="el-icon-success"></i>
            已成功提交保单，您需要支付保费金额200元
          </span>
        </div>
        <el-button @click="next" class="immBtn">立即支付</el-button>
      </el-dialog>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InsuranceForm',
  data () {
    return {
      // 表明index，从0开始
      activeIndex: 0,
      // 已成功提交保单弹出层默认隐藏
      centerDialogVisible: false,
      // 企业信息数据
      informationForm: {
        name: '',
        code: '',
        CorporateName: ''
      },
      // 项目信息数据
      sportsForm: {
        area: '',
        type: '',
        sportsname: '',
        sportsnumber: '',
        sportsmoney: '',
        sportsday: '',
        plight: '',
        valid: '',
        people: '',
        credit: '',
        mechanism: ''
      },
      // 企业信息数据内容校验
      informationRules: {
        name: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        code: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        CorporateName: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ]
      },
      // 项目信息数据内容的校验
      sportsRules: {
        area: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        type: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        sportsname: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        sportsnumber: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        sportsmoney: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        sportsday: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        plight: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        valid: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        people: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        credit: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ],
        mechanism: [
          { required: true, message: '请输入企业名称', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    // 重置表单
    Reset () {
      this.sportsForm.type = ''
    },
    // 跳到下一步
    next () {
      this.activeIndex = +this.activeIndex + 1 + ''
      // 支付的时候隐藏弹框
      this.centerDialogVisible = false
    },
    // 跳到上一步
    back () {
      this.activeIndex = +this.activeIndex - 1 + ''
    },
    handleClick () { },
    // 确认信息 弹框显示
    adddialog () {
      this.centerDialogVisible = true
    },
    // 返回首页
    first () {
      this.activeIndex = +this.activeIndex - 3 + ''
    }
  }
}
</script>

<style lang="less" scoped>
.cardForm {
  width: 1200px;
  // height: 1540px;
  box-sizing: border-box;
  background-color: rgba(255, 255, 255, 1);
  border-radius: 10px;

  .el-steps el-steps--horizontal {
    /deep/ .el-step__icon.is-text {
      color: rgba(153, 153, 153, 1);
      background: #fff;
      .el-step__icon-inner {
        font-size: 10px;
        font-weight: 400;
        // border:1px solid rgba(153,153,153,1);
      }
    }
  }
  /deep/ .el-tabs__nav-scroll {
    display: none;
  }
  /deep/ .el-dialog {
    position: relative;
    border-radius: 10px;
    width: 800px;
    height: 280px;
    .dialogbox {
      .dialogmoney {
        font-size: 24px;
        display: flex;
        justify-content: center;
        align-items: center;
        .el-icon-success {
          font-size: 40px;
          color: rgba(91, 193, 100, 1);
          margin-right: 14px;
        }
      }
    }

    .el-button {
      position: absolute;
      top: 176px;
      left: 330px;
      background-color: #316ceb;
      color: #fff;
      width: 140px;
      height: 40px;
    }
  }
  div#pane-1 {
    .return {
      margin-left: 410px;
      .el-button--danger {
        width: 160px;
        height: 40px;
        background: rgba(255, 255, 255, 1);
        border: 1px solid rgba(204, 204, 204, 1);
        margin-right: 60px;
        /deep/ span {
          font-size: 18px;
          font-family: PingFang SC;
          font-weight: 400;
          color: rgba(102, 102, 102, 1);
        }
      }
      .el-button--primary {
        width: 160px;
        height: 40px;
        background: rgba(49, 108, 235, 1);
        border-radius: 4px;
        margin-bottom: 46px;
        /deep/ span {
          font-size: 18px;
          font-family: PingFang SC;
          font-weight: 400;
          color: rgba(255, 255, 255, 1);
        }
      }
    }
  }
  div#pane-2 {
    padding: 0 110px 15px 40px;
    font-size: 20px;
    font-weight: 400;
    .means {
      font-size: 18px;
      font-family: PingFang SC;
      font-weight: 400;
      color: rgba(51, 51, 51, 1);
      margin-top: 27px;
      margin-bottom: 19px;
      display: block;
      float: left;
    }
    .sure {
      float: left;
      margin-top: 20px;
    }
    .payoff {
      margin: 0px 259px 0px 110px;
    }
    /deep/ p.payoffline {
      background: rgba(220, 220, 220, 1);
      height: 1px;
      margin-top: 15px;
    }
  }
  div#pane-3 {
    text-align: center;
    p {
      font-size: 20px;
      font-family: PingFang SC;
      font-weight: 400;
      color: rgba(102, 102, 102, 1);
      margin-bottom: 44px;
    }
    .success {
      width: 151px;
      height: 138px;
      background-color: pink;
      margin: 0 auto;
    }
    .orderDetails {
      margin-bottom: 100px;
      .homepage {
        margin-right: 60px;
      }
    }
  }
  /deep/ .el-form-item__label {
    text-align: right;
  }
  /deep/ .el-tabs__nav-wrap::after {
    width: 0px;
  }
  /deep/ .el-card__body {
    box-sizing: border-box;
  }
  .el-steps {
    text-align: center;
    padding: 40px 144px;
  }
  .cardarea {
    .information {
      background-color: rgba(245, 246, 248, 1);
      border-radius: 4px;
      margin: 0 30px;
      font-size: 22px;
      font-family: PingFang SC;
      font-weight: 500;
      color: rgba(51, 51, 51, 1);
      height: 54px;
      // text-indent: 1.25em;
    }
    .sports {
      background-color: rgba(245, 246, 248, 1);
      border-radius: 4px;
      margin: 0px 30px;
      font-size: 22px;
      font-family: PingFang SC;
      font-weight: 500;
      color: rgba(51, 51, 51, 1);
      height: 54px;
    }
    /deep/ .information-content {
      margin-top: 40px;
      margin-left: 177px;
      margin-bottom: 60px;
      .upload-demo {
        .el-button {
          width: 140px;
          height: 40px;
          background: rgba(255, 255, 255, 1);
          border: 1px solid rgba(204, 204, 204, 1);
          border-radius: 4px;
          font-size: 16px;
        }
        .el-upload__tip {
          font-size: 16px;
          width: 460px;
          height: 30px;
          background: rgba(245, 246, 248, 1);
          .el-icon-paperclip {
            font-size: 18px;
            margin-left: 20px;
          }
        }
        .xiazai {
          font-size: 14px;
          font-family: PingFang SC;
          font-weight: 400;
          color: rgba(102, 102, 102, 1);
          margin-right: 105px;
        }
      }
      .el-form-item {
        display: block;
        .paperclip {
          width: 460px;
          height: 30px;
          background: rgba(245, 245, 247, 1);
          margin-top: 5px;
          .el-icon-paperclip {
            font-size: 18px;
            margin-left: 20px;
          }
          span {
            font-size: 16px;
            font-family: PingFang SC;
            font-weight: 400;
            color: rgba(51, 51, 51, 1);
          }
        }
        .el-input__inner {
          width: 460px;
        }
      }
    }
    .sports-content {
      margin-top: 40px;
      margin-left: 129px;
      // margin-bottom: 60px;
      p {
        font-size: 16px;
        font-family: PingFang SC;
        font-weight: 400;
        color: rgba(51, 51, 51, 1);
      }
      .el-form-item {
        display: block;
        margin-bottom: 20px;
        .el-input {
          width: auto;
        }
        .xinyongcode {
          display: inline;
          text-decoration: underline;
          color: rgba(49, 108, 235, 1);
        }
        /deep/ .el-input__inner {
          width: 460px;
        }
      }
      .button {
        .el-button {
          width: 160px;
          height: 40px;
          margin-right: 60px;
        }
      }
    }
  }
}
</style>
