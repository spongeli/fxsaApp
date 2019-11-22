<template>
	<scroll-view class="index-scroll" scroll-x="true" :show-scrollbar="false">
		<block v-for="(item,index) in tabBars" :key="index">
			<view class="index-scroll-item">
				<text :class="{active:tabSelectIndex==index}" @tap="changScrollTab(index)">{{item.name}}</text>
			</view>
		</block>
	</scroll-view>
</template>

<script>
	export default {
		props: {
			tabBars: Array,
			tabSelectIndex: Number
		},
		methods: {
			changScrollTab(index) {
				this.$emit("changScrollTab", index);
			},
		}
	}
</script>

<style>
	.index-scroll {
		width: 750upx;
		height: 80upx;
		/* display: flex; */
		flex-direction: row;
		/* 段落中的文件不进行换行 */
		white-space: nowrap;
		overflow-x: hidden;
	}

	.index-scroll-item {
		/* 成块级元素不换行 */
		display: inline-block;
		flex-wrap: nowrap;
		line-height: 80upx;
		font-size: 35upx;
		padding: 0 25upx;
		font-size: #9B9B9B;
	}

	.index-scroll .active {
		color: #FFDF34;
		font-weight: bold;
		border-bottom: 5upx solid #FFDF34;
	}
</style>
