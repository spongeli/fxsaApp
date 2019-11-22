<template>
	<view class="index-message animated flipInY fast">
		<view class="message-list1 v-fjs">
			<view class="v-fc">
				<image :src="item.userPic" mode="widthFix"></image>
				<view>{{item.userNick}}</view>
			</view>
			<template v-if="!item.isGuanzhu">
				<view class="v-fc">
					<view  @tap="guanzhu" class="index-follow">+关注</view>
					<view @tap="quixiaoguanzhu" class="f35">×</view>
				</view>
			</template>
		</view>
		<view @tap="toDetail" class="message-list2">{{item.title}}</view>
		<view class="message-list3 v-fjc">
			<image @tap="toDetail" :src="item.messageSrc" mode="widthFix"></image>
			<!-- 中间的视屏播放按钮 -->
			<template v-if="item.messageType == 'video'">
				<view class="icon iconfont icon-bofang index-message-center-button"></view>
				<view class="index-message-center-data">{{item.videoInfo.srcanNum}} 次播放 {{item.videoInfo.timeLong}}</view>
			</template>
		</view>
		<view class="message-list4 v-fjs">
			<view class="v-fc">
				<view @tap="dingcai('ding')" class="icon iconfont icon-smile" :class="{active:(item.messageInfo.operaType == 1)}">{{item.messageInfo.dingNum}}</view>
				<view @tap="dingcai('cai')" class="icon iconfont icon-kulian" :class="{active:(item.messageInfo.operaType == 2)}">{{item.messageInfo.caiNum}}</view>
			</view>
			<view class="v-fc">
				<view class="icon iconfont icon-pinglun1">{{item.commentNum}}</view>
				<view class="icon iconfont icon-zhuanfa">{{item.shareNum}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: Object,
			index: Number
		},
		methods: {
			// 关注
			guanzhu() {
				this.item.isGuanzhu = true;
				uni.showToast({
					title: "关注成功"
				});
			},
			// 顶踩
			dingcai(type) {
				switch (type) {
					case "ding":
						if (this.item.messageInfo.operaType == 1) {
							return
						}
						this.item.messageInfo.dingNum++;
						if (this.item.messageInfo.operaType == 2) {
							this.item.messageInfo.caiNum--;
						}
						this.item.messageInfo.operaType = 1;
						break;
					case "cai":
						if (this.item.messageInfo.operaType == 2) {
							return
						}
						this.item.messageInfo.caiNum++;
						if (this.item.messageInfo.operaType == 1) {
							this.item.messageInfo.dingNum--;
						}
						this.item.messageInfo.operaType = 2;
						break;
				}
			},
			// 跳转详情页
			toDetail(){
				console.log("跳转详情页！！");
			},
			// ×操作
			quixiaoguanzhu(){
				this.item.isGuanzhu = true;
			}
		}
	}
</script>

<style>
	.index-message {
		padding: 20upx;
		border-bottom: 1px solid #EEEEEE;
	}

	.message-list1>view:first-child>image {
		width: 88upx;
		height: 88upx;
		border-radius: 100%;
		margin-right: 20upx;
	}

	.message-list1>view>:last-child {
		color: #989898;
	}

	.index-follow {
		width: 80upx;
		padding: 0 10upx;
		color: #000000;
		background-color: #F4F4F4;
		border-radius: 5upx;
		margin-right: 10upx;
	}

	.message-list2 {
		margin-top: 15upx;
	}

	.message-list3 {
		position: relative;
	}

	.message-list3 image {
		width: 100%;
		margin-top: 15upx;
		border-radius: 10upx;
	}

	.index-message-center-button {
		position: absolute;
		font-size: 130upx;
		color: white;
	}

	.index-message-center-data {
		position: absolute;
		bottom: 8upx;
		right: 8upx;
		padding: 0 15upx;
		font-size: 16upx;
		background-color: rgba(51, 51, 51, 0.78);
		color: white;
		border-radius: 10upx;
	}

	.message-list4 {
		color: #D5D5D5;
	}

	.message-list4 .active {
		color: #FFDF34;
	}

	.message-list4>view>view:first-child {
		margin-right: 15upx;
	}
</style>
