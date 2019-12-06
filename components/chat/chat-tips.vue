<template>
	<view>
		<view class="chat-right-tips-mask" v-show="show" @tap="cancel"></view>
		<view class="chat-right-tips" v-show="show">
			<view class="icon iconfont icon-sousuo v-fc" @tap="addUser">
				<view>加糗友</view>
			</view>
			<view class="icon iconfont icon-qingchu v-fc" @tap="deleteUnReader">
				<view>清除未读</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			show: {
				type: Boolean,
				default: false
			}
		},
		methods: {
			cancel() {
				this.$emit("cancel");
			},
			addUser() {
				this.$emit("addUser");
			},
			deleteUnReader() {
				this.$emit("deleteUnReader");
			}
		}
	}
</script>
<style>
	.chat-right-tips-mask {
		position: fixed;
		right: 0;
		left: 0;
		top: 0;
		bottom: 0;
		z-index: 1999;
	}

	.chat-right-tips {
		position: fixed;
		width: 350upx;
		height: 200upx;
		top: 88upx !important;
		right: 0;
		z-index: 2000;
		background-color: #FFFFFF;
		box-shadow: 1upx 1upx 20upx 2upx #CCCCCC;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.chat-right-tips>view {
		font-size: 40upx;
		margin-left: 20upx;
	}

	.chat-right-tips>view>view {
		font-size: 35upx;
		margin-left: 20upx;
	}

	.chat-right-tips>view:first-child {
		margin-top: 30upx;
	}

	.chat-right-tips>view:last-child {
		margin-bottom: 30upx;
	}
</style>
