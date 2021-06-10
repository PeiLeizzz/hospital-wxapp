<!-- 该页面是通过底部弹出框切换挂号进去的入口
 1、关于insureVisited = 0时是按科室进去
 2、关于insureVisited = 1时是搜医生进去
 3、关于insureVisited = 2时是按日期进去
 4、关于insureVisited = 3时是按专科进去
 -->
<template>
	<view>
		<!-- 背景图片 -->
		<image class="background" mode="widthFix" src="../../../static/appointment/home_home.png"></image>

		<!-- 搜索框 -->
		<view class="search-box row-box" :class="searchClass">
			<input placeholder="按专家名字搜索" placeholder-class="search-placeholder" @click="searchFocus" @blur="searchBlur"
			 confirm-type="search" @input="searchKey"></input>
			<icon class="iconfont icon-sousuo"></icon>

			<view class="search-list" v-if="searchDoctor.length">
				<view v-for="item in searchDoctor" :key="key" bind="">
					<!-- 这边绑定搜索结果页面 -->
					<navigator url="">
					</navigator>
				</view>
			</view>

			<view class="search-list" v-else>
				<view v-for="item in searchDoctor" :key="key" bind="">
					未搜索到包含此关键词的专家!
				</view>
			</view>
		</view>

		<!-- 咨询栏 -->
		<view class="consulting-type row-box clearfix">
			<view>
				<navigator url="">
					<icon class="iconfont icon-zhuanjia"></icon>
					<text>专家咨询</text>
				</navigator>
			</view>

			<view>
				<navigator url="">
					<icon class="iconfont icon-Micon-zixun"></icon>
					<text>快速咨询</text>
				</navigator>
			</view>
		</view>

		<view class="four-list row-box clearfix">
			<view class="four-list-tag">
				<text>按科室选择</text>
				<navigator url="" class="four-list-all">
					<text>更多</text>
					<icon class="iconfont icon-fangxiangyou"></icon>
				</navigator>
			</view>

			<view class="four-list-icon">
				<view v-for="item in department" :key="key">
					<navigator url="">
						<icon class="iconfont" :class="'icon-' + item.icon"></icon>
						<text>{{item.tag}}</text>
					</navigator>
				</view>
			</view>
		</view>

		<view class="four-list row-box clearfix">
			<view class="four-list-tag">
				<text>推荐医生</text>
				<view class="four-list-all">
					<text>更多</text>
					<icon class="iconfont icon-fangxiangyou"></icon>
				</view>
			</view>

			<view class="four-list-icon">
				<view>
					<image src="/static/appointment/avatar_1.jpg"></image>
					<text>医生1</text>
				</view>
				<view>
					<image src="/static/appointment/avatar_0.jpg"></image>
					<text>医生2</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgUrl: '/static/appointment/',
				department: [{
					tag: "皮肤科",
					icon: "pifuke color1"
				}, {
					tag: "推拿",
					icon: "tuina color2"
				}, {
					tag: "骨科",
					icon: "guke color3"
				}, {
					tag: "耳鼻咽喉",
					icon: "erbihouke color4"
				}, {
					tag: "检验",
					icon: "jianyan color5"
				}, {
					tag: "B超",
					icon: "Bchaoyuyue-K color6"
				}, {
					tag: "科室7",
					icon: "wrong color7"
				}, {
					tag: "科室8",
					icon: "wrong color8"
				}],
			}
		},
		methods: {
			// 搜索栏聚焦
			searchFocus: function() {
				this.searchClass = "inputFocus"
			},
			// 搜索栏失焦
			searchBlur: function() {
				this.searchClass = ""
			},
			// 搜索关键词
			searchKey: function(e) {
				console.log(e)
			}
		}
	}
</script>

<style lang="scss">
	@import '@/common/scss/common.scss';

	page {
		--shadow-color: rgba(0, 0, 0, .15);
		--main-icon-color: #4684f7;
		--main-font-color: #11cd6e;
		--main-fontSelect-color: #a9b7b7;
		background-color: #f7f7f7;
	}

	/* 背景 */
	.background {
		position: absolute;
		top: 0;
		left: 0;
		width: 750rpx;
		// z-index: -1;
	}

	.backgroundColor {
		position: absolute;
		z-index: -1;
		top: 0;
		left: 0;
		width: 100vw;
		height: 120rpx;
		background-color: #b5cfff;
	}

	/* 修复浮动 */
	.clearfix::after {
		content: '';
		display: block;
		width: 100%;
		height: 100%;
		clear: both;
	}

	/* 主盒子 */
	.row-box {
		width: 94vw;
		min-height: 30rpx;
		margin: 0 auto;
		background-color: white;
		border-radius: 10rpx;
		box-shadow: 0 2px 5px var(--shadow-color);
	}

	/* 搜索栏 */
	.search-box {
		position: absolute;
		top: 270rpx;
		width: 90vw;
		margin: 0 5vw;
		padding: 0;
		background-color: white;
		transition: .25s;
	}

	.search-box input {
		height: 70rpx;
		padding: 0 40px 0 .5em;
		color: #555;
	}

	.search-box .icon-sousuo {
		position: absolute;
		top: 0;
		right: 0;
		padding: 0 25rpx;
		line-height: 70rpx;
		font-size: 40rpx;
		color: #888;
	}

	.search-placeholder {
		color: #ddd;
	}

	.search-list {
		display: none;
	}

	.inputFocus {
		position: fixed;
		transform: translateY(-100px);
		border-radius: 50px;
		box-shadow: 2px 2px 5px 1600px rgba(0, 0, 0, .2);
	}

	.inputFocus .search-list {
		position: absolute;
		display: block;
		width: 100%;
		margin-top: 3px;
		color: #555;
		background-color: white;
		border-radius: 5px;
		box-shadow: 2px 2px 5px rgba(0, 0, 0, .3);
	}

	.inputFocus .search-list>view {
		margin: 0 20rpx;
		padding: 10rpx;
		border-bottom: 1px solid #eee;
	}

	.inputFocus .search-list>view text {
		color: red;
	}

	/* 咨询 */
	.consulting-type {
		margin-top: 400rpx;
		padding: 20rpx 0;
	}

	.consulting-type>view {
		float: left;
		width: 50%;
		padding: 0 20px;
		text-align: center;
		line-height: 60rpx;
		color: #555;
		box-sizing: border-box;
		font-size: 40rpx;
		text-shadow: 1px 2px 1px var(--shadow-color);
		transition: 0.5s;
	}

	.consulting-type>view icon {
		margin-right: 15rpx;
	}

	.consulting-type>view:nth-child(2) {
		border-left: 1px solid #eee;
	}

	.consulting-type>view:active {
		color: #474747;
		text-shadow: 0 0 1px #a9b7b7;
	}

	/* 四列列表 */
	.four-list {
		margin-top: 25rpx;
		padding: 0;
		font-size: 30rpx;
	}

	.four-list-tag {
		display: flex;
		justify-content: space-between;
		align-items: center;
		width: 95%;
		margin: 0 2.5%;
		padding: 20rpx 10rpx;
		text-align: left;
		color: #888;
		font-weight: bold;
		border-bottom: 1px solid #eee;
	}

	.four-list .four-list-tag>view>text:active,
	.four-list .four-list-tag>view>text:active+icon {
		color: #666;
	}

	.four-list-all .icon-fangxiangyou {
		font-size: 15px;
		margin: -17rpx 0 0 10rpx;
	}

	.four-list-all {
		color: #ccc;
		font-weight: normal;
		text-shadow: none;
		font-size: 15px;
	}

	.four-list-icon>view {
		float: left;
		width: 25%;
		padding: 15rpx 10rpx;
		box-sizing: border-box;
		text-align: center;
		color: #777;
	}

	.four-list-icon icon:nth-child(1),
	.four-list-icon image,
	.user-icon {
		display: block;
		width: 50rpx;
		height: 50rpx;
		margin: 0 auto 10rpx;
		padding: 20rpx;
		color: rgba(255, 255, 255, .8);
		font-size: 50rpx;
		text-align: center;
		background-color: #149be7;
		border-radius: 50rpx;
		box-shadow: 0 2px 3px var(--shadow-color);
		text-shadow: 1px 1px 2px rgba(0, 0, 0, .3);
		transition: .1s;
	}

	.four-list>view icon:nth-child(1):active {
		text-shadow: .5px .5px 1px rgba(0, 0, 0, .6);
		box-shadow: 0 3px 10px rgba(0, 0, 0, .3)
	}

	.four-list>view image,
	.user-icon {
		padding: 0;
		width: 90rpx;
		height: 90rpx;
		background-color: #fff;
		border: 1px solid #eee;
	}
</style>
