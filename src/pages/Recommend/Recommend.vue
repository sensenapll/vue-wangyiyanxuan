<template>
  <div class="reco-container">
    <HeaderSlot>
      <div class="header-title" slot="headerTitle">
        <!-- <span :class="{on:  isOn}" @click="gotoFindOrSelect(true)">发现</span> -->
        <span :class="{on:  !isOn}" @click="gotoFindOrSelect(false)">值得买</span>
      </div>
    </HeaderSlot>
    <router-view />
  </div>
</template>
<script>
  export default {
    data () {
      return {
        isOn: true
      }
    },
    mounted () {
      // 识物页面初始显示时即请求数据,为路由组件使用数据做准备
      this.$store.dispatch('getRecommendTabs');
      this.$store.dispatch('getRecommends');
    },
    // methods: {
    //   gotoFindOrSelect (isGoToFind) {
    //     this.isOn = !this.isOn;
    //     if (isGoToFind) {
    //       // 跳转到find--发现页面
    //         this.$router.push('/recommend/find');
    //     } else {
    //       // 跳转到select--甄选页面
    //       this.$router.push('/recommend/select');
    //     }
    //   }
    // }
  }
</script>
<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import "../../common/stylus/mixins.styl";
  .reco-container
    padding-bottom 100px
</style>
