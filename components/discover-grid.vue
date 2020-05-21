<template>
	<view class="discover-grid">
		<view class="date-picker-wrap">
			<DatePicker :dateInfo="date" @dateChange="dateChange"></DatePicker>
		</view>
		<view class="false"></view>
		<view class="list-wrap">
			<view v-for="(i, k) in info" :key="k" >
				<!-- #ifdef MP-WEIXIN -->
				<ListGrid :dateInfo="i.date" v-if="i.date===date">
				<!-- #endif -->
				<!-- #ifndef MP-WEIXIN -->
				<ListGrid :dateInfo="i.date" v-show="i.date===date">
				<!-- #endif -->
					<view
						v-for="(item, index) in i.list"
						:key="index"
					>
						<List01
							category="normal"
							:idx="index"
							:title="item.title"
							:desc="item.author"
							:pic="item.pic"
						></List01>
					</view>

				</ListGrid>
			</view>
		</view>
	</view>
</template>

<script>
	import DatePicker from './date-picker.vue'
	import ListGrid from './list-grid.vue'
	import List01 from './list-components/list-01.vue'
	
	export default {
		components: { ListGrid, DatePicker, List01 },
		props: {
			info: {
				type: Array
			}
		},
		data() {
			return {
				date: '2020/04',
				// date: '2020/05',
			};
		},
		methods: {
			dateChange (date) {
				this.date = date.replace('-', '/')
				console.log((this.date))
			},
		}
	}
</script>

<style lang="stylus">
	.discover-grid
		position relative
		.date-picker-wrap
			position fixed
			top 88upx
			z-index 10
			width 680upx
		.false
			height 74upx
</style>
