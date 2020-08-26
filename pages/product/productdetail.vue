<template>
  <div class="container">
    <!-- 头部图片、导航区域 -->
    <div class="top">
      <!-- 图片展示区域 -->
      <div class="img"></div>
      <!-- 导航区域 -->
      <div class="navigation">
        <i class="el-icon-location"></i>
        <span>当前位置：产品中心 - 产品详情</span>
      </div>
    </div>
    <!-- 主体内容区域 -->
    <div class="content">
      <!-- 采购项目详情部分 -->
      <el-card style="marginBottom: 20px; borderRadius: 10px; padding: 30px">
        <p>泗县界牌张村张陶安置小区农民文化广场工程采购项目</p>
        <table
          v-for="(item,i) in tableDatas"
          :key="i"
          style="width: 100%; color: #656565"
          class="myTable"
        >
          <tr>
            <td class="column">项目编号</td>
            <td class="column">{{ item.num }}</td>
            <td class="column">项目状态</td>
            <td class="column">{{ item.state }}</td>
          </tr>
          <tr>
            <td class="column">招标人(公司)</td>
            <td class="column">{{ item.zbr }}</td>
            <td class="column">招标人(公司)统一社会信用代码</td>
            <td class="column">{{ item.abrty }}</td>
          </tr>
          <tr>
            <td class="column">招标代理</td>
            <td class="column">{{ item.zbdl }}</td>
            <td class="column">招标代理统一社会信用代码</td>
            <td class="column">{{ item.zbdlty }}</td>
          </tr>
          <tr>
            <td class="column">开标时间</td>
            <td class="column">{{ item.kbsj }}</td>
            <td class="column">投标有效期(天)</td>
            <td class="column">{{ item.tbyxq }}</td>
          </tr>
          <tr>
            <td class="column">保证金全额(元)</td>
            <td class="column">{{ item.bzjje }}</td>
            <td class="column">保证金缴纳截止日期</td>
            <td class="column">{{ item.bzjjn }}</td>
          </tr>
        </table>
        <el-row type="flex" style="color: #656565; marginTop: 17px">
          <el-col style="textAlign: left">
            预计应缴纳保费：
            <span style="color: red">{{ price }}</span>元
          </el-col>
          <el-col style="textAlign: right">更新时间：2020-08-09</el-col>
        </el-row>
        <el-button
          style="width: 140px; backgroundColor: #316BEB; fontSize: 18px"
          type="primary"
        >申请购买</el-button>
      </el-card>
      <!-- 产品详情、重要说明、保险条款费率部分 -->
      <el-card style="borderRadius: 10px; padding: 30px; marginBottom: 40px">
        <el-tabs v-model="activeName" type="card" @tab-click="handleClick">
          <el-tab-pane label="产品详情" name="first">
            <div style="marginBottom: 40px">
              <div style="fontSize: 20px; fontWeight: bold; lineHeight: 30px; color: #333333">产品解读</div>
              <div
                style="fontSize: 16px; lineHeight: 30px; color: #656565"
              >投标保证保险是指保险公司向工程项目招标人提供的保证工程项目投标人履行投标义务的保险。一旦投标人未履行投标义务导致招标人产生损失时，保险公司向招标人承担代偿责任。</div>
            </div>
            <div style="marginBottom: 40px">
              <div style="fontSize: 20px; fontWeight: bold; lineHeight: 30px; color: #333333">保险公司</div>
              <div
                style="fontSize: 16px; lineHeight: 30px; color: #656565"
              >本产品为《建设工程施工合同履约保证保险（A款）》《投标保证保险条款(2016版)》，由中国太平洋财产保险股份有限公司云南分公司承保份额44%、中国人民财产保险股份有限公司云南省分公司承保份额20%、诚泰财产保险股份有限公司云南分公司承保份额16%、中国平安财产保险股份有限公司云南分公司承保份额12%、中华联合财产保险股份有限公司云南分公司承保份额4%、阳光财产保险股份有限公司云南省分公司承保份额为4%，6家保险公司共同承保。其中，中国太平洋财产保险股份有限公司云南分公司为首席承保公司（主承保公司），共保体其他成员公司均为共保人。</div>
            </div>
            <div>
              <div style="fontSize: 20px; fontWeight: bold; lineHeight: 30px; color: #333333">保险责任 （施工方）</div>
              <div style="fontSize: 16px; lineHeight: 30px; color: #656565">
                建设工程施工类项目保障内容：
                根据《中华人民共和国招标投标法》、《中华人民共和国招标投标法实施条例》，在保险期间内，投保人在向被保险人招标建设工程投标的过程中，因下列情形之一给被保险人造成经济损失的，被保险人可向保险人提出索赔，保险人按照保险合同的约定承担赔偿责任：<br />
                （一）投标截止后投保人未经被保险人同意或者违反《建设工程项目招标文件》撤销投标文件；<br />
                （二）中标后未按《建设工程项目招标文件》的要求签署《建设工程施工合同》；<br />
                （三）投保人弄虚作假行为，但尚未构成犯罪；<br />
                （四）投保人与其他投标人相互串通投标，但尚未构成犯罪；<br />
                （五）《建设工程招标文件》规定的其他有关投标实质性违约情形。<br />
                建设工程非施工类项目保障内容：<br />
                在保险期间内，投保人在取得被保险人提出的招标文件、参加投标的过程中，因下列情形给被保险人造成直接经济损失的，被保险人可向保险人提出索赔，保险人依据本保险合同的约定，在保险金额内承担损失赔偿责任：<br />
                （一）投保人在投标截止后违反招标文件撤销投标文件；<br />
                （二）投保人在中标后未按照招标文件约定与被保险人订立合同；<br />
                （三）投保人违反了招标文件规定的其他有关投标的实质性约定；<br />
              </div>
            </div>
          </el-tab-pane>
          <el-tab-pane label="重要说明" name="second">重要说明</el-tab-pane>
          <el-tab-pane label="保险条款费率" name="third">保险条款费率</el-tab-pane>
        </el-tabs>
      </el-card>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // 采购项目详情数据
      tableDatas: [{
        num: 'SXCG2020332',
        state: '正常',
        zbr: '泗县墩集镇人民政府',
        abrty: '11341324003203292D',
        zbdl: '上海容基工程项目管理有限公司',
        zbdlty: '91310114703275983G',
        kbsj: '2020-08-18',
        tbyxq: '',
        bzjje: '15000',
        bzjjn: '2020-08-18'
      }],
      // 预计应缴纳保费金额
      price: 200,
      // tab条当前展示页
      activeName: 'first'
    }
  },
  methods: {
    handleClick (tab, event) {
      console.log(tab, event)
    }
  }
}
</script>

<style lang="less" scoped>
.container {
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
    text-align: center;
    padding-top: 40px;
    background-color: #f6f7f8;
    .el-card {
      width: 1200px;
      margin: 0 auto;
      p {
        font-size: 24px;
        font-weight: bold;
        // text-align: center;
        margin-bottom: 30px;
      }
      .myTable {
        border-collapse: collapse;
        margin: 0 auto;
        text-align: center;
        tr {
          td {
            border: 1px solid #cad9ea;
            color: #666;
            height: 60px;
            padding: 0 16px;
          }
          :nth-child(odd) {
            text-align: right;
          }
          :nth-child(even) {
            text-align: left;
          }
        }
      }
    }
    /deep/ .is-active {
      color: #ffffff;
      background-color: #316beb;
    }
    /deep/ .el-tabs__item {
      font-size: 18px;
    }
    .el-tab-pane {
      padding: 30px;
      text-align: left;
      // font-size: 16px;
      // background-color: #ccc;
      // border: 1px solid #000;
    }
  }
}
</style>
