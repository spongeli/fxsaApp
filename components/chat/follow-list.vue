<template>
	<view class="follow-item v-fjs">
		<image :src="item.userpic" mode="widthFix"></image>
		<view class="follow-center">
			<view>{{item.username}}</view>
			<view class="icon iconfont" :class="{'icon-nan':item.sex == 1,'icon-nv':item.sex == 0}">{{item.age}}</view>
		</view>
		<view class="icon iconfont" :class="{'icon-zengjia1':item.type == 2,'icon-xuanze-yixuan':item.type != 2}"></view>
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
	.follow-item {
		padding: 20upx 0;
		border-bottom: 3upx solid #EEEEEE;
	}

	.follow-item>image {
		width: 160upx;
		border-radius: 100%;
	}

	.follow-item>view:last-child {
		font-size: 35upx;
		color: #F8791B;
	}

	.follow-center {
		margin: 0 30upx;
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.follow-center>view:first-child {
		font-size: 35upx;
	}

	.follow-center>view:last-child {
		width: 50upx;
		text-align: center;
		margin-top: 20upx;
		font-size: 16upx;
		color: #FFFFFF;
		background-color: #43B3FF;
		padding: 0 5upx;
		border-radius: 15upx;
	}

	.icon-xuanze-yixuan {
		color: #CCCCCC !important;
	}
</style>
