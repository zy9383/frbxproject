<template>
  <div class="register">
    <div class="lefttitle">丰融保险保函</div>
    <!-- 注册表单区域 -->
    <div class="box">
      <div class="boxtitle">丰融保险保函</div>
      <el-form :model="ruleForm" :rules="rules" ref="ruleForm">
        <!-- 手机号 -->
        <el-form-item label prop="phone">
          <el-input v-model="ruleForm.phone" placeholder="手机号"></el-input>
        </el-form-item>
        <!-- 短信验证码 -->
        <el-form-item label prop="message">
          <el-input style="width: 220px" v-model="ruleForm.message" placeholder="短信验证码"></el-input>
          <el-button style="float: right" type="primary">发送验证码</el-button>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item label prop="password">
          <el-input
            type="password"
            v-model="ruleForm.password"
            placeholder="8-20位密码，字母/数字/符号至少2种"
            suffix-icon="el-icon-date"
          ></el-input>
        </el-form-item>
        <!-- 勾选框 -->
        <el-checkbox v-model="checked">
          <span style="color: #666666">我已阅读并接受</span>
          <span style="color: #316CEB">丰融保险保函用户协议</span>
        </el-checkbox>
        <!-- 注册按钮 -->
        <el-button type="primary" style="width: 100%; margin: 30px 0 15px" :disabled="btnstatus">注册</el-button>
        <!-- 马上登录 -->
        <p style="textAlign: right; color: #666666">
          已有账号，
          <a style="color: #316CEB; marginLeft: -10px" href="#">马上登录</a>
        </p>
      </el-form>
    </div>
    <!-- 版权部分 -->
    <div class="little">版权所有©建设工程信息服务平台 CopyRight© All Rights Reserved 京ICP备11004160号-3</div>
  </div>
</template>

<script>
export default {
  data () {
    // 手机号验证
    const checkPhone = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('手机号不能为空'))
      } else {
        const phoneReg = /^(?:(?:\+|00)86)?1(?:(?:3[\d])|(?:4[5-7|9])|(?:5[0-3|5-9])|(?:6[5-7])|(?:7[0-8])|(?:8[\d])|(?:9[1|8|9]))\d{8}$/
        if (phoneReg.test(value)) {
          callback()
        } else {
          return callback(new Error('请输入正确的手机号'))
        }
      }
    }
    // 密码验证
    // const checkPassword = (rule, value, callback) => {
    //   if (!value) {
    //     return callback(new Error('手机号不能为空'))
    //   } else {
    //     const passwordReg = /^1[3|4|5|7|8][0-9]\d{8}$/
    //     if (passwordReg.test(value)) {
    //       callback()
    //     } else {
    //       return callback(new Error('请输入正确的手机号'))
    //     }
    //   }
    // }
    return {
      ruleForm: {
        phone: '',
        message: '',
        password: ''
      },
      rules: {
        phone: [
          { required: true, validator: checkPhone, trigger: 'blur' }
        ],
        message: [
          { required: true, message: '请输入验证码', trigger: 'blur' }
        ]
      },
      btnstatus: true
    }
  }
}
</script>

<style lang="less" scoped>
.register {
  position: relative;
  width: 1920px;
  height: 1080px;
  background: url(../../assets/registerbg.png) no-repeat;
  .lefttitle {
    position: absolute;
    left: 180px;
    top: 60px;
    color: #ffffff;
    font-size: 35px;
  }
  .box {
    position: absolute;
    top: 286px;
    right: 300px;
    width: 440px;
    height: 468px;
    padding: 0 40px;
    background-color: #ffffff;
    border-radius: 10px;
    .boxtitle {
      font-size: 29px;
      color: #333333;
      text-align: center;
      margin: 47px 0;
    }
  }
  .little {
    position: absolute;
    bottom: 88px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 14px;
    color: #ffffff;
  }
}
</style>
