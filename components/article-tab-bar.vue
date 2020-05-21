<template>
	<view class="article-tab-bar">
		<view class="comment-button">写一个评论..</view>
		<view class="function-wrap">
			<PanelFunction :category="5"></PanelFunction>
		</view>
	</view>
</template>

<script>
	import PanelFunction from './panel-function.vue'
	
	export default {
		components: { PanelFunction },
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="stylus">
	.article-tab-bar
		position relative
		display flex
		padding 18upx 35upx
		box-sizing border-box
		width 750upx
		height 100upx
		background-color rgb(251, 251, 251)
		border-top 1upx solid #eee
		.comment-button
			box-sizing border-box
			padding-left 30upx
			width 280upx
			height 64upx
			line-height 64upx
			border 1upx solid #999999
			border-radius 5px
			font-size 14px
			color #999
		.function-wrap
			position absolute
			right 55upx
</style>
