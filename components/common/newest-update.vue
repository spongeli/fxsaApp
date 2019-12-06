<template>
	<view class="newest-update">
		<view>最近更新</view>
		<block v-for="(item,index) in newestList" :key="index">
			<view class="newest-update-item v-f" @tap="toTopic">
				<image :src="item.src" mode="widthFix" lazy-load></image>
				<view>
					<view>{{item.contextHeader}}</view>
					<view>{{item.contextTitle}}</view>
					<view>{{item.contextFooter}}</view>
				</view>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		props: {
			newestList: Array
		},
		methods:{
			toTopic(){
				uni.navigateTo({
					url:"/pages/topic/topic"
				})
			}
		}
	}
</script>

<style scoped>
	/* 最新更新 */
	.newest-update {
		width: 97%;
		padding-left: 20upx;
		margin-top: 20upx;
	}

	.newest-update>view:first-child {
		font-size: 30upx;
	}

	.newest-update-item {
		margin-top: 45upx;
		padding-bottom: 20upx;
		border-bottom: 5upx solid #EEEEEE;
	}

	.newest-update-item image {
		width: 180upx;
		border-radius: 15upx;
	}

	.newest-update-item>view {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin-left: 40upx;
		padding: 25upx 0;
	}

	.newest-update-item>view>view {
		color: #A4A4A4;
		font-size: 20upx;
	}

	.newest-update-item>view>view:first-child {
		font-size: 35upx;
		color: #000000;
	}
</style>
