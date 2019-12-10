<template>
	<view>
		<!-- 导航栏 -->
		<index-nav-bar direction="left" leftType="icon-fanhui" rightType="icon-guanbi" placeholder=" 搜索糗友" fontColor="#000000"
		 @clickLeftIcon="clickLeftIcon" @clickRightIcon="clickRightIcon" disabledFlag="false"></index-nav-bar>

		<!-- 导航 -->
		<view class="dynamic-navbar v-fjs">
			<block v-for="(item,index) in tabBars" :key="index">
				<view :class="{'active':index == tabSelectIndex}" @tap="changScrollTab(index)">{{item.name}}</view>
			</block>
		</view>

		<!-- 列表 -->
		<view class="dynamic-span">
			<block v-for="(items,indexs) in tabBarScorllSpan" :key="indexs">
				<template v-if="indexs == tabSelectIndex">
					<block v-for="(item,index) in items.list" :key="index">
						<follow-list :item="item"></follow-list>
					</block>
					<load-more :loadMore="items.loadMore"></load-more>
				</template>
			</block>
		</view>
	</view>
</template>

<script>
	import indexNavBar from "../../components/common/index-nav-bar.vue"
	import followList from "../../components/chat/follow-list.vue";
	import loadMore from "../../components/common/load-more.vue"
	export default {
		components: {
			indexNavBar,
			followList,
			loadMore
		},
		data() {
			return {
				tabSelectIndex: 0,
				tabBars: [{
						name: '互关',
						id: 'huguan'
					},
					{
						name: '关注',
						id: 'guanzhu'
					},
					{
						name: '粉丝',
						id: 'fensi'
					}
				],
				tabBarScorllSpan: [{
					loadMore: "正在加载更多",
					list: [{},{}]
				}, {
					loadMore: "正在加载更多",
					list: [{}]
				}, {
					loadMore: "正在加载更多",
					list: [{}]
				}]
			}
		},
		methods: {
			clickLeftIcon() {
				uni.navigateBack({
					delta: 1
				})
			},
			clickRightIcon() {
				uni.navigateBack({
					delta: 1
				})
			},
			changScrollTab(index) {
				this.tabSelectIndex = index;
			}
		}
	}
</script>

<style>
	.dynamic-navbar {
		width: 400upx;
		margin: 0 auto;
		margin-top: 25upx;
	}

	.dynamic-navbar>view {
		font-size: 35upx;
		font-weight: bold;
		padding: 0 8upx;
		color: #949494;
	}

	.dynamic-navbar .active {
		color: #343434;
		border-bottom: 8upx solid #FEDE33;
	}
	
	.dynamic-span{
		width: 686upx;
		margin: 0 30upx;
	}
</style>
