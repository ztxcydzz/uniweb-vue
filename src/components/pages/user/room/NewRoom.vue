<template lang="pug">
#new-room
  el-steps.steps(:active="stepIndex", :align-center="true", :center="true")
    el-step(v-for="(item, index) of steps", :title="item", discription="", :key="item.id")
  router-view
</template>

<script>
  export default {
    computed: {
      stepIndex () {
        const route = this.$route.path.split('/')[4]
        if (route === 'member') return 2
        else if (route === 'confirm') return 3
        else if (route === 'publish') return 4
        else return 1
      }
    },
    data () {
      return {
        steps: ['填写基本信息', '成员信息', '确认', '发布']
      }
    }
  }
</script>

<style lang="stylus" scoped>
#new-room
  .steps
    width 100%
    margin-top 10px
    padding 15px 7%
    background white
    text-align center
  .white-wrap
    background white
</style>
