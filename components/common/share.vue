<template>
	<view class="share-span">
		<view class="">分享到</view>
		<scroll-view class="share-scroll-view" scroll-x="true">
			<view class="share-item">A</view>
			<view class="share-item">B</view>
			<view class="share-item">C</view>
		</scroll-view>
		<view class="">取消</view>
	</view>
</template>

<script>
</script>

<style>
	.share-span {
		position: fixed;
		z-index: 1001;
		left: 0;
		right: 0;
		bottom: 0;
		background-color: #FFFFFF;
		text-align: center;
	}
	.share-scroll-view{
		width: 750upx;
		/* display: flex; */
		/* 段落中的文件不进行换行 */
		white-space: nowrap;
		overflow-x: hidden;
	}
	.share-item{
		display: inline-block;
		flex-wrap: nowrap;
	}
</style>
