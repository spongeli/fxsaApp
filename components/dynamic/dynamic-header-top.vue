<template>
	<view>
		<view class="topic-bg">
			<image :src="item.picsrc" mode="aspectFill"></image>
		</view>
		<view class="topic-header v-f">
			<image :src="item.picsrc" mode="widthFix"></image>
			<view>#{{item.title}}#</view>
		</view>
		<view class="topic-header-text">
			<view>动态 {{item.dynamicNum}} 今日 {{item.scanNum}}</view>
			<view>{{item.context}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: Object
		}
	}
</script>

<style>
	.topic-bg {
		width: 100%;
		height: 300upx;
		overflow: hidden;
	}

	.topic-bg>image {
		width: 100%;
		filter: blur(10px);
	}

	.topic-header>view {
		line-height: 65upx;
		font-size: 35upx;
		margin-left: 30upx;
	}

	.topic-header image {
		width: 150upx;
		margin-left: 30upx;
		margin-top: -75upx;
		border-radius: 20upx;
		z-index: 999;
	}

	.topic-header-text {
		height: 150upx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin: 0 30upx;
		padding-top: 20upx;
	}

	.topic-header-text>view:first-child {
		color: #D3D3D3;
		letter-spacing: 1upx;
	}

	.topic-header-text>view:last-child {
		color: #A3A3A3;
		line-height: 40upx;
		font-size: 30upx;
		letter-spacing: 2upx;
	}
</style>
