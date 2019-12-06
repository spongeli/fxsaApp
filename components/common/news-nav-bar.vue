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
				<view class="center-icon">
					<block v-for="(item,index) in tabBers" :key="index">
						<view @tap="changtabIndex(index)" :class="{'active':index==tabBerIndex}">{{item.name}}</view>
					</block>
				</view>
			</block>
			<block slot="right">
				<view class="icon iconfont icon-bianji1 right-icon" @tap="toPublish"></view>
			</block>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from "../uni-nav-bar/uni-nav-bar.vue";
	export default {
		components: {
			uniNavBar
		},
		props: {
			tabBers: Array,
			tabBerIndex: Number
		},
		methods: {
			// 切换话题
			changtabIndex(index) {
				this.$emit("changtabIndex", index);
			},
			toPublish() {
				uni.navigateTo({
					url: "../../publish/publish"
				})
			}
		}
	}
</script>

<style scoped>
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
		display: flex;
		justify-content: center;
	}
	
	.center-icon>view{
		padding: 0 5upx;
		height: 66upx;
		font-size: 40upx;
		color: #969696;
		font-weight: bold;
	}
	
	.center-icon>view:first-child {
		margin-right: 20upx;
	}

	.center-icon .active {
		color: #343434;
		border-bottom: 8upx solid #FEDE33;
	}

	/* 导航栏样式 end */
</style>
