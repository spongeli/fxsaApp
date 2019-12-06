<template>
	<view>
		<!-- 导航栏 -->
		<index-nav-bar></index-nav-bar>

		<!-- 导航组件 -->
		<index-scroll :tabBars="tabBars" :tabSelectIndex="tabSelectIndex" @changScrollTab="changScrollTab"></index-scroll>
		<!-- swiper 面板 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:windowHeight + 'px'}" :current="tabSelectIndex" @change="changSwiper">
				<swiper-item v-for="(items,index) in tabBarScorllSpan" :key="index">
					<scroll-view class="list" scroll-y="true" show-scrollbar="false" @scrolltolower="scrollPull(index)">
						<template v-if="items.list.length>0">
							<!-- 列表 -->
							<block v-for="(item,index1) in items.list" :key="index1">
								<index-list :item="item" :index="index"></index-list>
							</block>
							<!-- 加载更多 -->
							<load-more :loadMore="items.loadMore"></load-more>
						</template>
						<!-- 什么都没有的默认页 -->
						<template v-else>
							<no-thing></no-thing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import indexList from "../../../components/index/index-list/index-list.vue";
	import indexScroll from "../../../components/index/index-scroll/index-scroll.vue";
	import loadMore from "../../../components/common/load-more.vue";
	import noThing from "../../../components/common/no-thing.vue";
	import uniNavBar from "../../../components/uni-nav-bar/uni-nav-bar.vue";
	import indexNavBar from "../../../components/common/index-nav-bar.vue"
	export default {
		components: {
			indexList,
			indexScroll,
			loadMore,
			noThing,
			uniNavBar,
			indexNavBar
		},
		data() {
			return {
				windowHeight: 0,
				tabSelectIndex: 0,
				tabBarScorllSpan: [{
						loadMore: "正在加载更多",
						list: [{
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: false,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 0, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}, {
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: false,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 0, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}, {
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: true,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 1, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}]
					},
					{
						loadMore: "正在加载更多",
						list: [{
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: false,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 0, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}, {
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: true,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 1, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}]
					},
					{
						loadMore: "正在加载更多",
						list: [{
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: false,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 0, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}, {
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: true,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 1, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}, {
							userPic: "../../../static/userpic/1.jpg",
							userNick: "昵称",
							isGuanzhu: false,
							title: "发表内容发表内容发表内容发表内容发表内容",
							messageType: "img", // img:图片   video:视屏
							messageSrc: "../../../static/datapic/11.jpg",
							videoInfo: {
								srcanNum: "10w",
								timeLong: "2:47"
							},
							messageInfo: {
								operaType: 0, // 0:未操作  1：顶 2：踩
								dingNum: 100,
								caiNum: 10
							},
							commentNum: 303,
							shareNum: 12
						}]
					},
					{
						loadMore: "正在加载更多",
						list: []
					},
					{
						loadMore: "正在加载更多",
						list: []
					},
					{
						loadMore: "正在加载更多",
						list: []
					},
					{
						loadMore: "正在加载更多",
						list: []
					},
					{
						loadMore: "正在加载更多",
						list: []
					}
				],
				tabBars: [{
						name: '关注',
						id: 'guanzhu'
					},
					{
						name: '推荐',
						id: 'tuijian'
					},
					{
						name: '体育',
						id: 'tiyu'
					},
					{
						name: '热点',
						id: 'redian'
					}, {
						name: '财经',
						id: 'caijing'
					}, {
						name: '娱乐',
						id: 'yule'
					}, {
						name: '军事',
						id: 'junshi'
					}, {
						name: '历史',
						id: 'lishi'
					}
				]
			}
		},
		methods: {
			changScrollTab(index) {
				this.tabSelectIndex = index;
			},
			changSwiper(e) {
				this.tabSelectIndex = e.target.current;
			},
			scrollPull(index) {
				if (this.tabBarScorllSpan[index].loadMore != '正在加载更多') {
					return;
				}
				this.tabBarScorllSpan[index].loadMore = '加载中';

				// 模拟数据加载
				setTimeout(() => {
					var obj = {
						userPic: "../../../static/userpic/1.jpg",
						userNick: "昵称",
						isGuanzhu: false,
						title: "发表内容发表内容发表内容发表内容发表内容",
						messageType: "img", // img:图片   video:视屏
						messageSrc: "../../../static/datapic/11.jpg",
						videoInfo: {
							srcanNum: "10w",
							timeLong: "2:47"
						},
						messageInfo: {
							operaType: 0, // 0:未操作  1：顶 2：踩
							dingNum: 100,
							caiNum: 10
						},
						commentNum: 303,
						shareNum: 12
					}

					this.tabBarScorllSpan[index].list.push(obj);
					this.tabBarScorllSpan[index].loadMore = '正在加载更多';
				}, 1000);
				// this.tabBarScorllSpan[index].loadMore = '没有数据啦';
			},
			toPublish() {
				uni.navigateTo({
					url: "../../publish/publish"
				})
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(80);
					this.windowHeight = height;
				}
			});
		},
		// 监听原生导航栏按钮事件
		onNavigationBarButtonTap(e) {
			switch (e.index) {
				// 发布事件
				case 1:
					uni.navigateTo({
						url: "../../publish/publish"
					});
					break;
					// 签到
				case 0:
					break;
			}
		},
		// 监听原生导航栏click事件
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url: "../../search/search"
			})
		}
	}
</script>

<style>
	
</style>
