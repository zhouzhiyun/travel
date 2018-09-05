<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon icon-fanhui"></div>
        </div>
        <div class="header-input">
            <span class="iconfont icon-sousuo"></span>
            输入城市/主题/游玩景点
        </div>
        <router-link to="/city">
            <div class="header-right">
                {{city}}
                <span class="iconfont icon-jiantou arrow-icon"></span>
            </div>
        </router-link>
    </div>
</template>
<script>
import { mapState } from "vuex";
export default {
  name: "HomeHeader",
  computed: {
    ...mapState(["city"])
  }
};
</script>
<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
.header
    display: flex
    line-height: $headerHeight
    background: $bgColor
    color: #fff
    height: $headerHeight
    .header-left
        width: 0.64rem
        float: left
        .back-icon
            text-align: center
            font-size: 0.4rem
    .header-input
        flex: 1
        height: 0.64rem
        line-height: 0.64rem
        margin-top: 0.12rem
        margin-left: 0.12rem
        background: #ffffff
        border-radius: 0.1rem
        color: #ccc
        padding-left: 0.12rem
    .header-right
        min-width: 1.04rem
        padding: 0 0.1rem
        float: right
        text-align: center
        color: #fff
        .arrow-icon
            font-size: 0.24rem
            margin-left: -0.04rem
</style>
