<template>
    <div class="header">
        城市选择
        <router-link to="/" class="header-left">
            <div class="iconfont back-icon icon-fanhui"></div>
        </router-link>
    </div>
</template>
<script>
export default {
  name: 'CityHeader',
  
};
</script>
<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		overflow:hidden
		height: $headerHeight
		line-height: $headerHeight
		text-align: center
		color:#fff
		background: $bgColor
		font-size:.32rem
		border:none
		.header-left
			width:.64rem
			float:left
			.back-icon
				text-align:center
				font-size:0.4rem
				color:#fff
</style>
