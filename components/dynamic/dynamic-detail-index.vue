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
					<view class="header-text">
						<view class="header-name">{{dynamicInfos.nickName}}</view>
						<view class="header-time">{{ZHmessageTime}}</view>
					</view>
					<view class="icon iconfont" :class="{'icon-nan':dynamicInfos.sex == 1,'icon-nv':dynamicInfos.sex == 0}">{{dynamicInfos.age}}</view>
				</view>
				<template v-if="!dynamicInfos.isGuanZhu">
					<view class="icon iconfont icon-zengjia dynamic-right-header-guanzhu" @tap="guanzhu">关注</view>
				</template>
			</view>
			<!-- 右侧内容 -->
			<view @tap="toDynamicDetail">{{dynamicInfos.title}}</view>

			<!-- 非转发，视频和图片的信息 -->
			<template v-if="dynamicInfos.mediaType != 'share'">
				<view class="dynamic-right-media v-fjc">
					<view class="dynamic-image-list">
						<block v-for="(item,index) in item.mediaSrcList" :key="index">
							<image :src="item" lazy-load mode="widthFix" @tap="scanImage(index)"></image>
						</block>
					</view>
					<template v-if="dynamicInfos.mediaType == 'video'">
						<image :src="dynamicInfos.mediaSrc" mode="widthFix"></image>
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
			<!-- 脚 -->
			<view class="v-fjs dynamic-right-foot">
				<view><span>{{dynamicInfos.addressProvince}}</span><span>{{dynamicInfos.addressCity}}</span></view>
				<view class="v-fjs">
					<view class="icon iconfont icon-zhuanfa">{{dynamicInfos.commentInfo.zhanfaNum}}</view>
					<view class="icon iconfont icon-pinglun1" @tap="commonClick">{{dynamicInfos.commentInfo.pinglunNum}}</view>
					<view class="icon iconfont icon-ccdbaa">{{dynamicInfos.commentInfo.dianzanNum}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import time from "../../common/time.js"
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
			toDynamicDetail() {
				console.log("xingqing")
			},
			scanImage(index) {
				uni.previewImage({
					urls: this.item.mediaSrcList,
					current: index,
					indicator: 'default',
					loop: true
				})
			},
			commonClick(){
				this.$emit("commonClick");
			}
		},
		computed: {
			ZHshareText: function() {
				if (this.dynamicInfos.mediaType == 'share') {
					var text = this.dynamicInfos.shareText;
					return text.length <= 33 ? text : (text.substring(0, 33) + "...");
				}
				return "";
			},
			ZHmessageTime: function() {
				return time.gettime.getDateDifference(this.item.messageTime);
			}
		}
	}
</script>

<style>
	@import url("../../common/dynamic-common.css");

	.dynamic-back {
		padding-bottom: 20upx;
		border-bottom: 4upx solid #EEEEEE;
	}

	.dynamic-right-header {
		height: 100upx;
	}

	.dynamic-right {
		border-bottom: none;
	}

	.header-text {
		margin-top: -10upx;
		display: flex;
		justify-content: space-between;
		flex-flow: column;
	}

	.header-time {
		color: #CDCDCD;
	}

	.dynamic-right-header>view:first-child {
		height: auto;
	}

	.dynamic-image-list {
		box-sizing: border-box;
		width: 100%;
		padding: 10upx;
	}

	.dynamic-image-list>image {
		width: 100%;
		border-radius: 15upx;
	}
</style>
