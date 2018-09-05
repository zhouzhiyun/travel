<template>
    <div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom">
					当前城市
				</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">
							{{this.$store.state.city}}
						</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">
					热门城市
				</div>
				<div class="button-list">
					<div class="button-wrapper" 
						v-for="item of hot" 
						:key="item.id"
						@click="handleCityClick(item.name)"
					>
						<div class="button">
							{{item.name}}
						</div>
					</div>
				</div>
			</div>
			<div class="area" 
				v-for="(item, key) of cities" 
				:key="key"
				:ref="key"
			>
				<div class="title border-topbottom">
					{{key}}
				</div>
				<div class="item-list" 
					v-for="innerItem of item" 
					:key="innerItem.id"
					@click="handleCityClick(innerItem.name)"
				>
					<div class="item border-bottom">{{innerItem.name}}</div>
				</div>
				
			</div>
		</div>
    </div>
</template>
<script>
import BScroll from "better-scroll";
import { mapState, mapMutations } from "vuex";
export default {
  name: "CityList",
  props: {
    cities: Object,
    hot: Array,
    letter: String
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper);
  },
  computed: {
    ...mapState({
      currentCity: "city"
    })
  },
  methods: {
    handleCityClick(city) {
      this.changeCity(city);
      this.$router.push("/");
    },
    ...mapMutations(["changeCity"])
  },
  watch: {
    letter() {
      if (this.letter) {
        const element = this.$refs[this.letter][0];
        this.scroll.scrollToElement(element);
      }
    }
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.border-topbottom
	&:before
		border-color: #ccc
	&:after
		border-color: #ccc
.list
	overflow: hidden
	position: absolute
	top: 1.58rem
	left: 0
	right: 0
	bottom: 0
	.border-bottom
		&:before
			border-color: #ccc
	.title
		background-color: #eee
		line-height: 0.54rem
		padding-left: 0.2rem
		color: #666
		font-size: 0.26rem
	.button-list
		overflow: hidden
		padding: 0.1rem 0.6rem 0.1rem 0
		.button-wrapper
			float: left
			width: 33.33%
			.button
				margin: 0.1rem
				text-align: center
				padding: 0.1rem 0
				border: 0.02rem solid #ccc
				border-radius: 0.06rem
	.item-list
		.item
			padding-left: 0.2rem
			line-height: 0.76rem
</style>
