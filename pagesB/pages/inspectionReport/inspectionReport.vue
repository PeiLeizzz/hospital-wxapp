<template>
	<view>
		<view class="report-item" v-for="item in reportList" :class="'report-item-background-' + item.color">
			<view class="report-item-text">
				<view class="report-name">{{ item.name }}</view>
				<view class="report-detail" :class="'report-detail-background-' + item.color"> 
					{{ item.detail }}
				</view>
			</view>
			<view class="report-check" :class="'report-check-background-'+item.color">
				<navigator :url="item.url">立即查看</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				reportList: [
					{
						"name": "影像报告",
						"detail": "影像报告，在线查看",
						"url": "../reportQuery/reportQuery",
						"color": "blue"
					},
					{
						"name": "心脏彩超",
						"detail": "ct检查报告，实时查看",
						"url": "../reportQuery/reportQuery",
						"color": "green"
					},
					{
						"name": "核医学报告",
						"detail": "核医学检查报告，在线查看",
						"url": "../reportQuery/reportQuery",
						"color": "brown"
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.report-item {
		margin: 20rpx 15rpx 20rpx;
		padding: 20rpx 25rpx 20rpx;
		border: #E7EBED;
		border-radius: 20px;
		height: 200rpx;
		width: 90%;
	}
	
	.report-item-text {
		display: inline-block;
		width: 70%;
	}
	
	.report-name {
		line-height: 125rpx;
		font-size: 40rpx;
		padding-left: 30rpx;
	}
	
	.report-detail {
		line-height: 50rpx;
		font-size: 20rpx;
		padding-left: 30rpx;
	}
	
	.report-check {
		color: white;
		font-size: 25rpx;
		border-radius: 25px;
		text-align: center;
		display: inline-block;
		width: 25%;
		height: 50rpx;
		line-height: 50rpx;
		padding: 5rpx 10rpx 10rpx 5rpx;
	}
	
	.report-item-background-blue {
		background-color: rgb(238,245,254);
	}
	
	.report-item-background-green {
		background-color: rgb(238,250,248);
	}
	
	.report-item-background-brown {
		background-color: rgb(254,251,238);
	}
	
	.report-check-background-blue {
		background-color: rgb(91,138,197);
	}
	
	.report-check-background-green {
		background-color: rgb(124,184,169);
	}
	
	.report-check-background-brown {
		background-color: rgb(203,170,84);
	}
	
	.report-detail-background-blue {
		color: rgb(91,138,197);
	}
	
	.report-detail-background-green {
		color: rgb(124,184,169);
	}
	
	.report-detail-background-brown {
		color: rgb(203,170,84);
	}
</style>
