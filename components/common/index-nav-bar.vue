<template>
	<view>
		<!-- 自定义导航 -->
		<view class="status_bar">
			<!-- 这里是状态栏 -->
		</view>
		<uni-nav-bar :fixed="true" :border="false">
			<!-- 左边 -->
			<block slot="left">
				<view class="icon iconfont icon-qiandao left-icon"></view>
			</block>
			<block>
				<view class="center-icon" @tap="clickInput">
					<input type="text" value="" placeholder=" 搜索糗事" placeholder-class="icon iconfont icon-sousuo center-icon-place" disabled="true"/>
				</view>
			</block>
			<block slot="right">
				<view class="icon iconfont icon-bianji1 right-icon" @tap="toPublish"></view>
			</block>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from "../uni-nav-bar/uni-nav-bar.vue"
	export default {
		components:{
			uniNavBar
		},
		methods:{
			toPublish() {
				uni.navigateTo({
					url: "../../publish/publish"
				})
			},
			clickInput(){
				uni.navigateTo({
					url:"../../search/search"
				})
			}
		}
	}
</script>

<style>
	/* 导航栏样式 start */
	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}
	
	.left-icon {
		width: 100%;
		font-size: 45upx;
		color: #FF9619;
		text-align: center;
	}
	
	.right-icon {
		width: 100%;
		font-size: 45upx;
		text-align: center;
	}
	.center-icon {
		width: 100%;
		height: 70upx;
		background-color: #F7F7F7;
		text-align: center;
		border-radius: 15upx;
	}
	.center-icon>input {
		width: 100%;
		height: 100%;
		font-size: 25upx;
	}
	.center-icon-place{
		font-size: 30upx;
		color: #CCCCCC;
	}
	/* 导航栏样式 end */
</style>
