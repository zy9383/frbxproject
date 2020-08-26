<template>
  <div class="container">
    <div class="loginbox">
      <div class="login-header">
        <span class="fricon"></span>
        <span class="guarantee">丰融保险保函</span>
      </div>
      <!-- tabs栏 -->
      <el-tabs v-model="activeName">
        <!-- 短信登录 -->
        <el-tab-pane label="短信登录" name="first">
          <el-form :model="smsLogin" :rules="smsRules" ref="smsRuleRef">
            <el-form-item prop="phoneNumber">
              <el-input v-model="smsLogin.phoneNumber" placeholder="请输入手机号" class="content"></el-input>
            </el-form-item>
          </el-form>
          <el-form :model="smsLogin" :rules="smsRules" ref="smsRuleRef">
            <el-form-item prop="yanzhencode">
              <el-input
                v-model="smsLogin.yanzhencode"
                placeholder="请输入验证码"
                class="verificationCode"
              ></el-input>
              <el-button class="send">发送验证码</el-button>
            </el-form-item>
          </el-form>
          <div class="formal">
            <el-button>登录</el-button>
            <el-button>注册</el-button>
          </div>
        </el-tab-pane>
        <!-- 短信登录 -->

        <!-- 密码登录 -->
        <el-tab-pane label="密码登录" name="second">
          <el-form :model="smsLogin1" :rules="smsRules1" ref="smsRuleRef1">
            <el-form-item prop="phoneNumber1">
              <el-input v-model="smsLogin1.phoneNumber1" placeholder="手机号" class="content"></el-input>
            </el-form-item>
          </el-form>
          <el-form :model="smsLogin1" :rules="smsRules1" ref="smsRuleRef1">
            <el-form-item prop="yanzhencode1">
              <el-input
                v-model="smsLogin1.yanzhencode1"
                placeholder="图形验证码"
                class="verificationCode"
              ></el-input>
              <span class="graph">ghryt</span>
            </el-form-item>
          </el-form>
          <el-form :model="smsLogin1" :rules="smsRules1" ref="smsRuleRef1">
            <el-form-item prop="password">
              <el-input v-model="smsLogin1.password" placeholder="密码" show-password></el-input>
            </el-form-item>
          </el-form>
          <div class="formal">
            <el-button>登录</el-button>
          </div>
          <div class="move">
            <el-checkbox v-model="checked">记住密码</el-checkbox>
            <span @click="removepassword">忘记密码</span>
            <span>注册</span>
          </div>
        </el-tab-pane>
        <!-- 密码登录 -->

        <!-- 扫码登陆 -->
        <el-tab-pane label="扫码登录" name="third">
          <div class="scanCode">
            <div class="erweima"></div>
            <div class="text">
              <p>请使用微信扫描二维码登录</p>
              <p class="text2">“丰融保险保函”</p>
            </div>
            <p class="newaccount">注册新账号</p>
          </div>
        </el-tab-pane>
        <!-- 扫码登陆 -->
      </el-tabs>
    </div>
    <!-- 忘记密码弹出层 -->
    <el-dialog title="忘记密码" :visible.sync="removedialogVisible" width="800px" :show-close="false">
      <p></p>
      <el-form
        :model="removeruleForm"
        :rules="removeRules"
        ref="removeRef"
        label-width="100px"
        class="demo-ruleForm"
      >
        <el-form-item label="手机号:" prop="mobile">
          <el-input v-model="removeruleForm.mobile"></el-input>
        </el-form-item>
        <el-form-item label="短信验证码:" prop="message">
          <el-input v-model="removeruleForm.message" class="message"></el-input>
          <el-button class="send">发送验证码</el-button>
        </el-form-item>
        <el-form-item label="新密码:" prop="newpassword">
          <el-input v-model="removeruleForm.newpassword"></el-input>
        </el-form-item>
        <el-form-item label="确认新密码:" prop="surepassword">
          <el-input v-model="removeruleForm.surepassword"></el-input>
        </el-form-item>
      </el-form>
      <p></p>
      <span slot="footer" class="dialog-footer">
        <el-button @click="resetdialogVisible">取 消</el-button>
        <el-button type="primary" @click="removedialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // tabs切换条默认显示first
      activeName: 'first',
      // 记住密码
      checked: 'true',
      // 忘记密码弹框的默认隐藏
      removedialogVisible: false,
      // 短信登陆数据
      smsLogin: {
        phoneNumber: '',
        yanzhencode: '',
      },
      // 密码登录数据
      smsLogin1: {
        phoneNumber1: '',
        yanzhencode1: '',
        password: ''
      },
      // 忘记密码数据
      removeruleForm: {
        mobile: '',
        message: '',
        newpassword: '',
        surepassword: ''
      },
      // 忘记密码校验规则
      removeRules: {
        mobile: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
          { required: true, type: 'number', message: '手机号必须为数字' }
        ],
        message: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
        ],
        newpassword: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
        ],
        surepassword: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
        ]
      },
      // 短信登陆校验规则
      smsRules:{
        phoneNumber: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
        ],
        yanzhencode: [
          { required: true, message: '请输入活动名称', trigger: 'blur' }
        ]
      },
      // 密码登录校验规则
      smsRules1: {
        phoneNumber1: [
          { required: true, message: '请输入活动名称', trigger: 'blur' },
        ],
        yanzhencode1: [
          { required: true, message: '请输入活动名称', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入活动名称', trigger: 'blur' }
        ]
      },
    }
  },
  methods: {
    // 让弹框显示
    removepassword() {
      this.removedialogVisible = true
    },
    // 重置表单
    resetdialogVisible() {
      this.removedialogVisible = false
      this.$refs.removeRef.resetFields();
    }
  }
}
</script>

<style lang="less" scoped>
.container {
  width: 1920px;
  height: 1080px;
  background-color: #eee;
  position: relative;
  .loginbox {
    width: 440px;
    height: 440px;
    background: rgba(255, 255, 255, 1);
    border-radius: 10px;
    position: absolute;
    top: 286px;
    left: 1180px;
    right: 300px;
    // bottom: 354px;
    .login-header {
      margin-top: 40px;
      margin-left: 108px;
      display: flex;
      .fricon {
        display: inline-block;
        width: 42px;
        height: 42px;
        background-color: pink;
      }
      .guarantee {
        font-size: 30px;
        font-family: Tensentype MingSongJ-W8;
        font-weight: 800;
        color: rgba(51, 51, 51, 1);
        margin-left: 8px;
        vertical-align: center;
      }
    }
    .el-tabs.el-tabs--top {
      padding: 40px;
      /deep/ .el-tabs__item.is-active {
        font-weight: 500;
        color: #316ceb;
      }
      /deep/ .el-tabs__active-bar {
        background-color: #316ceb;
        height: 3px;
      }
      /deep/ .el-tabs__item {
        color: rgba(102, 102, 102, 1);
        font-family: PingFang SC;
        font-weight: 400;
      }
      /deep/ div#pane-first {
        .formal {
          button.el-button.el-button--default {
            width: 360px;
            background: #dcdcdc;
            font-size: 16px;
          }
          /deep/ .el-button + .el-button {
            background-color: #fff !important;
            margin-left: 0px;
            margin-top: 19px;
            border: none;
          }
        }
        .content {
          margin-top: 20px;
        }
        /deep/ .verificationCode {
          // margin-top: 10px;
          width: 220px;
          margin-right: 15px;
        }
        .send {
          width: 120px;
          background: rgba(49, 108, 235, 1);
          border-radius: 4px;
          font-size: 16px;
          font-family: PingFang SC;
          font-weight: 400;
          color: rgba(255, 255, 255, 1);
        }
      }

      /deep/ div#pane-second {
        .formal {
          button.el-button.el-button--default {
            width: 360px;
            background: #dcdcdc;
            font-size: 16px;
          }
        }
        .content {
          margin-top: 20px;
        }
        /deep/ .verificationCode {
          // margin-top: 10px;
          width: 220px;
          margin-right: 15px;
        }
        .graph {
          display: inline-block;
          width: 120px;
          border-radius: 4px;
          background-color: #ccc;
        }
        .move {
          span {
            display: inline-block;
            font-size: 10px;
            color: #606266;
          }
        }
      }
      /deep/ div#pane-third {
        .scanCode {
          .erweima {
            width: 120px;
            height: 120px;
            background-color: #ffffff;
            margin: 15px 120px 12px 120px;
          }
          .text {
            width: 168px;
            height: 38px;
            font-size: 14px;
            font-family: PingFang SC;
            font-weight: 400;
            color: rgba(102, 102, 102, 1);
            margin: 0px 96px 27px 96px;
            .text2 {
              margin-left: 25px;
            }
          }
          .newaccount {
            font-size: 16px;
            font-family: PingFang SC;
            font-weight: 400;
            color: rgba(51, 51, 51, 1);
            margin: 0px 140px 0px 140px;
            cursor: pointer;
          }
        }
      }
      /deep/ div#tab-second {
        padding: 0px 51px;
        font-size: 18px;
      }
      /deep/ div#tab-first {
        font-size: 18px;
        .button.el-button.el-button--default.is-plain {
          width: 360px;
          height: 40px;
        }
      }
      /deep/ div#tab-third {
        font-size: 18px;
      }
    }
  }
  /deep/ .el-dialog {
    /deep/ .el-dialog__body {
      padding: 0;
      p {
        height: 1px;
        background: rgba(220, 220, 220, 1);
        margin-top: 19px;
      }
    }
    .demo-ruleForm {
      .message.el-input {
        input.el-input__inner {
          width: 320px;
        }
      }
      .send {
        width: 120px;
        background: rgba(49, 108, 235, 1);
        border-radius: 4px;
        font-size: 16px;
        font-family: PingFang SC;
        font-weight: 400;
        color: rgba(255, 255, 255, 1);
      }
      .el-input {
        width: 460px;
      }
    }
    form.el-form.demo-ruleForm {
      padding: 30px 0px 0px 117px;
    }
    .el-dialog__footer {
      margin-top: 20px;
    }
  }
}
</style>
