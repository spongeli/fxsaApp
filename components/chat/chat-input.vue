<template>
	<!-- 底部输入框 -->
	<view class="chat-input-foot v-f">
		<input type="text" value="" placeholder="文明发言" v-model="text" />
		<view class="icon iconfont icon-fabu" @tap="submit"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text: ''
			}
		},
		methods: {
			submit() {
				if (this.text) {
					this.$emit("submit", this.text);
					this.text = '';
				}
			}
		},
		onNavigationBarSearchInputConfirmed() {
			console.log(this.text);
		}
	}
</script>

<style>
	.chat-input-foot {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		width: 750upx;
		border-top: 3upx solid #EEEEEE;
		height: 90upx;
		line-height: 90upx;
	}

	.chat-input-foot input {
		height: 60upx;
		margin: auto 0;
		margin-left: 20upx;
		width: 560upx;
		background-color: #F7F7F7;
		border-radius: 15upx;
		padding: 0 20upx;
	}

	.chat-input-foot>view {
		flex: 1;
		text-align: center;
		font-size: 40upx;
	}
</style>
