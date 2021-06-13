<template>
	<view>
		<!-- 顶部导航栏 -->
		<view class="horizonal-tab">
			<scroll-view scroll-x="true" scroll-with-animation class="scroll-tab">
				<block v-for="(item,index) in tabBars" :key="index">
					<view class="scroll-tab-item" :class="{'active': tabIndex==index}" 
					@tap="toggleTab(index)">
						{{item.name}}
						<view class="scroll-tab-line"></view>
					</view>
				</block>
			</scroll-view>
		</view>
		
		<view class="select-area">
			<view class="area">院区</view>
			<picker mode="selector" class="select-content" :range="areas" @change="changeArea">
				{{ areas[index] }} >
			</picker>
		</view>
		
		<view v-if="hasContent" class="content">
			
		</view>
		
		<view v-else class="no-content">
			<view class="no-content-text-1">你还没有相关的订单</view>
			<view class="no-content-text-2">可以去其他地方看看</view>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				tabIndex: 0, /* 选中标签栏的序列,默认显示第一个 */
				contentList: [
					"近两周",
					"近两月",
					"近半年",
					"自定义"
				],
				tabBars:[
					{
						name: '近两周',
						id: 'twoWeeks'
					},
					{
						name: '近两月',
						id: 'twoMonths'
					},
					{
						name: '近半年',
						id: 'halfYear'
					},
					{
						name: '自定义',
						id: 'timeDIY'
					}
				],
				areas: [
					"鼓楼医院本部",
					"鼓楼江北国际分院"
				],
				index: 0,
				areaName: "鼓楼医院本部",
				hasContent: false
			}
		},
		methods:{
			//切换选项卡
			toggleTab (index) { 
				this.tabIndex = index;
			},
			//滑动切换swiper
			tabChange (e) { 
				console.log(e);
				this.tabIndex = e.detail.current;
			},
			changeArea (a) {
				this.index = a.detail.value;
			}
		}
	}
</script>

<style>
	.horizonal-tab{
		font-size: 35rpx;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		padding-left: 20rpx;
	}
	.horizonal-tab .active{
		color: #007AFF;
	}
	.scroll-tab{
		white-space: nowrap; /* 必要，导航栏才能横向*/
		border-bottom: 1rpx solid #eee;
		/* text-align: center; */
	}
	.scroll-tab-item{
		display: inline-block; /* 必要，导航栏才能横向*/
		margin: 20rpx 30rpx 0 30rpx;
	}
	.active .scroll-tab-line{
		border-bottom: 3rpx solid #007AFF;
		border-top: 3rpx solid #007AFF;
		border-radius: 20rpx;
		width: 100rpx;
	}
	
	.select-area {
		margin: 20rpx;
		border-radius: 20rpx;
		padding: 20rpx 20rpx 10rpx;
		box-shadow: 1px 1px 2px 2px rgba(0, 0, 0, 0.1);
		height: 80rpx;
		font-size: 35rpx;
		line-height: 80rpx;
	}
	
	.area {
		display: inline-block;
		width: 50%;
	}
	
	.select-content {
		display: inline-block;
		width: 45%;
	}
	
	.no-content {
		height: 600rpx;
		text-align: center;
	}
	
	.no-content-text-1 {
		margin-top: 300rpx;
		margin-bottom: 20rpx;
		font-size: 35rpx;
	}
	
	.no-content-text-2 {
		font-size: 20rpx;
		color: #CCCCCC;
	}
</style>
