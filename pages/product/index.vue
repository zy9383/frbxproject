<template>
  <div>
    产品中心
    <insurance v-show="!isshow"  @isshow-handle='handle' />
    <InsuranceForm v-show="isshow" @goback='isshow = false' />
  </div>
</template>

<script>
import Insurance from '@/components/insurance/insurance.vue'
import InsuranceForm from '@/components/insurance-form/insurance-form.vue'
export default {
  components: {
    Insurance,
    InsuranceForm
  },
  data () {
    return {
      // 投保单默认隐藏
      isshow: false
    }
  },
  methods: {
    handle () {
      // 显示投保单
      this.isshow = true
    }
  }
}
</script>

<style lang="less" scoped>
</style>
