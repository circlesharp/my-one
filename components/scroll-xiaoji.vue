<template>
	<view>
		<scroll-view class="scroll-x"
			scroll-x
		>
			<view class="list-wrap">
				<view class="list-item">
					<List02 showEdit></List02>
				</view>
				<view class="list-item" v-for="(item, index) in info" :key="index">
					<List02 :pic="item.url" :text="item.text"></List02>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import List02 from './list-components/list-02.vue'
	
	import { mock_xiaoJi } from '../static/mock/mock_xiaoJi.js'
	
	export default {
		components: { List02 },
		data() {
			return {
				info: ''
			}
		},
		created () {
			this.getInfo()
		},
		methods: {
			getInfo () {
				this.info = mock_xiaoJi
				this.info.splice(0, 2)
			}
		}
	}
</script>

<style lang="stylus">
	.scroll-x
		height 264upx
		width 750upx
		.list-wrap
			display flex
			.list-item
				flex 0 0 280upx
				margin-left 40upx
				width 280upx
				height 264upx
				&:last-child
					padding-right 40upx
</style>
