<template>
	<view>
		<view class="status_bar"></view>
		<uni-nav-bar :fixed="true" :border="false">
			<!-- 左边 -->
			<block slot="left">
				<view class="icon iconfont left-icon" :class="[leftIcon]" @tap="leftClick"></view>
			</block>
			<block>
				<view class="nav-bar-center">{{ZHcenterText}}</view>
			</block>
			<block slot="right">
				<view class="right-icon">
					<view class="icon iconfont" :class="[rightIcon]" @tap="rightClick"></view>
				</view>
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
			leftIcon: {
				type: String,
				default: 'icon-user-detail'
			},
			rightIcon: {
				type: String,
				default: 'icon-zengjia'
			},
			centerText:String
		},
		methods:{
			leftClick(){
				this.$emit("leftClick");
			},
			rightClick(){
				this.$emit("rightClick");
			}
		},
		computed:{
			ZHcenterText:function(){
				if(this.centerText.length>10){
					return this.centerText.substring(0,10) + '...';
				}
				return this.centerText;
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
		font-size: 45upx;
		color: #000000;
	}

	.right-icon {
		width: 100%;
		text-align: right;
	}

	.right-icon>view {
		font-size: 45upx;
		font-weight: bold;
	}

	.nav-bar-center {
		width: 100%;
		display: flex;
		justify-content: center;
		font-size: 35upx;
	}

	/* 导航栏样式 end */
</style>
