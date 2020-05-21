<template>
	<view class="list-view masonry">
		<view class="side left" ref="left">
			
			<!-- #ifdef MP-WEIXIN -->
			<view v-for="(item, index) in xiaoJiInfo" :key="index">
				<view class='masonry-item' v-if="!(index % 2)">
			<!-- #endif -->
			<!-- #ifndef MP-WEIXIN -->
			<view v-for="(item, index) in leftList" :key="index">
				<view class='masonry-item'>
			<!-- #endif -->
					<List04
						size='masonry'
						:img="item.img"
						:title="item.title"
						:author="item.author"
						:date="item.date"
						:location="item.location"
						@theHeight="theHeight"
					></List04>
				</view>
			</view>

		</view>
		<view class="side right" ref="right">
			
			<!-- #ifdef MP-WEIXIN -->
			<view v-for="(item, index) in xiaoJiInfo" :key="index">
				<view class='masonry-item' v-if="(index % 2)">
			<!-- #endif -->
			<!-- #ifndef MP-WEIXIN -->
			<view v-for="(item, index) in rightList" :key="index">
				<view class='masonry-item'>
			<!-- #endif -->
					<List04
						size='masonry'
						:img="item.img"
						:title="item.title"
						:author="item.author"
						:date="item.date"
						:location="item.location"
						@theHeight="theHeight"
					></List04>
				</view>
			</view>

		</view>

	</view>
</template>

<script>
	import List04 from './list-components/list-04.vue'
	
	let leftHeight = 0
	let rightHeight = 0
	let heights = []

	export default {
		components: { List04 },
		props: {
			xiaoJiInfo: {
				type: Array
			}
		},
		data() {
			return {
				leftList: [],
				rightList: []
			}
		},
		mounted () {
			// #ifndef MP-WEIXIN
			this.makeMasonry()
			// #endif
		},
		methods: {
			makeMasonry () {
				this.xiaoJiInfo.forEach((item, index) => {
					let rate = this._getPicRate(item.img)
					// console.log(leftHeight, rightHeight)
					if (leftHeight <= rightHeight) {
						this.leftList.push(item)
						leftHeight += rate
					} else {
						this.rightList.push(item)
						rightHeight += rate
					}
				})
			},
			_getPicRate (url) {
				let pic = new Image()
				pic.src = url
				return pic.height / pic.width
			}
		}
	}
</script>

<style lang="stylus">
	.list-view.masonry
		display flex
		justify-content space-between
		.masonry-item
			margin-bottom 30upx
</style>
