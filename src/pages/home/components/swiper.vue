<template>
	<div class="wrapper">
		<swiper :options="swiperOption" v-if="showSwiper">
	    	<swiper-slide v-for="item of list" :key="item.id">
				<img class="swiper-img" :src="item.imgUrl" />
	    	</swiper-slide>
	    	<div class="swiper-pagination"  slot="pagination"></div>
  		</swiper>
	</div>
</template>
<script>
	export default {
		name: "HomeSwiper",
		props: {
			list: Array
		},
		data () {
			return {
				swiperOption: {
					loop: true,
					autoplay: 3000,
					direction: 'horizontal',
					autoHeight: true,
					mousewheelControl: true,
					pagination: '.swiper-pagination',
					observeParents: true,
				}				
			}
		},
		computed: {
			showSwiper () {
				return this.list.length
			}
		}
	};
</script>

<style lang="stylus" scoped>
	.wrapper >>> .swiper-pagination-bullet
		background: #fff
	.wrapper
		overflow: hidden
		height:0
		padding-bottom: 26.66666%
		background: #ccc
		.swiper-img
			display: block
			width: 100%
</style>