<template>
	<view class="dynamic-back v-f animated flipInY fast">
		<!-- 左侧头像 -->
		<view class="dynamic-left">
			<image :src="dynamicInfos.nickPick" mode="widthFix"></image>
		</view>
		<!-- 右侧内容 -->
		<view class="dynamic-right">
			<!-- 右侧昵称 -->
			<view class="v-fjs dynamic-right-header">
				<view class="v-f">
					<view>{{dynamicInfos.nickName}}</view>
					<view class="icon iconfont" :class="{'icon-nan':dynamicInfos.sex == 1,'icon-nv':dynamicInfos.sex == 0}">{{dynamicInfos.age}}</view>
				</view>
				<template v-if="!dynamicInfos.isGuanZhu">
					<view class="icon iconfont icon-zengjia dynamic-right-header-guanzhu" @tap="guanzhu">关注</view>
				</template>
			</view>
			<!-- 右侧内容 -->
			<view>{{dynamicInfos.title}}</view>

			<!-- 非转发，视频和图片的信息 -->
			<template v-if="dynamicInfos.mediaType != 'share'">
				<view class="dynamic-right-media v-fjc">
					<image :src="dynamicInfos.mediaSrc" mode="widthFix"></image>
					<template v-if="dynamicInfos.mediaType == 'video'">
						<view class="icon iconfont icon-bofang dynamic-right-media-center"></view>
						<view class="dynamic-right-media-time">{{dynamicInfos.videoInfo.playNum}} 次播放 {{dynamicInfos.videoInfo.playTime}}</view>
					</template>
				</view>
			</template>
			<template v-else>
				<view class="dynamic-right-media-share v-fc">
					<image :src="dynamicInfos.mediaSrc" mode="widthFix"></image>
					<view>{{ZHshareText}}</view>
				</view>
			</template>
			<view class="v-fjs dynamic-right-foot">
				<view><span>{{dynamicInfos.addressProvince}}</span><span>{{dynamicInfos.addressCity}}</span></view>
				<view class="v-fjs">
					<view class="icon iconfont icon-zhuanfa">{{dynamicInfos.commentInfo.zhanfaNum}}</view>
					<view class="icon iconfont icon-pinglun1">{{dynamicInfos.commentInfo.pinglunNum}}</view>
					<view class="icon iconfont icon-ccdbaa">{{dynamicInfos.commentInfo.dianzanNum}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: Object
		},
		data() {
			return {
				dynamicInfos: this.item
			}
		},
		methods: {
			guanzhu() {
				this.item.isGuanZhu = true;
				uni.showToast({
					title: "关注成功"
				})
			},
		},
		computed: {
			ZHshareText: function() {
				if (this.dynamicInfos.mediaType == 'share') {
					var text = this.dynamicInfos.shareInfo.text;
					return text.length <= 33 ? text : (text.substring(0, 33) + "...");
				}
				return "";
			}
		}
	}
</script>

<style>
	/* 动态内容 start */
	.dynamic-back {
		margin-top: 20upx;
		padding: 15upx 20upx 0 15upx;
	}

	.dynamic-left {
		padding-right: 10upx;
		width: 12%;
	}

	.dynamic-left image {
		width: 100%;
		border-radius: 100%;
	}

	.dynamic-right {
		padding-left: 5upx;
		padding-bottom: 10upx;
		width: 88%;
		border-bottom: 1upx solid #BBBBBB;
	}

	.dynamic-right-header>view:first-child {
		height: 50upx;
		line-height: 50upx;
		font-size: 30upx;
		margin-top: 10upx;
	}

	.dynamic-right-header>view:first-child>view:first-child {
		color: #999999;
		letter-spacing: 4upx;
		margin-right: 10upx;
		line-height: 40upx;
	}

	.dynamic-right-header>view:first-child>view:last-child {
		font-size: 25upx;
		background-color: #44B3FF;
		color: #FFFFFF;
		text-align: center;
		border-radius: 20upx;
		padding: 0 10upx;
		margin-bottom: 10upx;
		line-height: 30upx;
		height: 30upx;
	}

	.dynamic-right-header-guanzhu {
		background-color: #F4F4F4;
		color: #010101;
		padding: 0 10upx;
		border-radius: 15upx;
		font-size: 30upx;
	}

	.dynamic-right>view:nth-child(2) {
		font-size: 35upx;
		line-height: 45upx;
		letter-spacing: 2upx;
		margin: 10upx 0;
	}

	.dynamic-right-media {
		position: relative;
	}

	.dynamic-right-media-center {
		position: absolute;
		font-size: 130upx;
		color: white;
	}

	.dynamic-right-media-time {
		position: absolute;
		font-size: 25upx;
		bottom: 0;
		right: 8upx;
		color: #FFFFFF;
	}

	.dynamic-right>view:nth-child(3)>image {
		width: 100%;
		border-radius: 15upx;
	}

	.dynamic-right-foot {
		color: #BBBBBB;
		padding-top: 10upx;
	}

	.dynamic-right-foot>view:last-child>view {
		margin-left: 15upx;
		font-size: 30upx;
		line-height: 30upx;
	}

	.dynamic-right-foot>view:first-child>span:first-child {
		margin-right: 20upx;
	}

	.dynamic-right-media-share {
		width: 97%;
		background-color: #F7F7F7;
		padding: 10upx 10upx;
		border-radius: 10upx;
		height: 100upx;
	}

	.dynamic-right-media-share>image {
		width: 200upx !important;
		margin-right: 20upx;
	}

	.dynamic-right-media-share>view {
		width: 100%;
		font-size: 25upx;
		text-overflow: ellipsis;
	}

	/* 动态内容 end */
</style>
