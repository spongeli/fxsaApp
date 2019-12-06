<template>
	<view style="width: 746upx;">
		<!-- 动态页模糊页头 -->
		<dynamic-header-top :item="dynamicHeaderTop"></dynamic-header-top>

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
						<dynamic-list :item="item"></dynamic-list>
					</block>
					<load-more :loadMore="items.loadMore"></load-more>
				</template>
			</block>
		</view>
	</view>
</template>

<script>
	import dynamicHeaderTop from "../../components/dynamic/dynamic-header-top.vue";
	import dynamicList from "../../components/dynamic/dynamic-list.vue";
	import loadMore from "../../components/common/load-more.vue";
	export default {
		components: {
			dynamicHeaderTop,
			dynamicList,
			loadMore
		},
		data() {
			return {
				windowHeight: 0,
				tabSelectIndex: 0,
				dynamicHeaderTop: {
					picsrc: "/static/topicpic/13.jpeg",
					title: "忆往事，敬余生",
					dynamicNum: 793,
					scanNum: 60,
					context: "面试官:在电梯里巧遇马云你会做什么?90后女孩子的回答当场被录用"
				},
				tabBars: [{
						name: '默认',
						id: '最新'
					},
					{
						name: '更新',
						id: 'gengxin'
					}
				],
				tabBarScorllSpan: [{
					loadMore: "正在加载更多",
					list: [{
							nickPick: "/static/userpic/14.jpg",
							nickName: "昵称",
							sex: 1, // 性别<>0 = 女  1 = 男
							age: 25,
							isGuanZhu: false,
							title: "动态内容动态内容动态内容动态内容动态内容动态内容",
							mediaType: "share", // 媒体类型<>image=图片&video=视频&share=分享
							mediaSrc: "/static/datapic/15.jpg",
							shareInfo: {
								text: "信息信息信息信息信息息信信息信息信息信信息信息息信息信息信息信息息信息信息信息信息信息信息息信信息信息信息信信息信息息信息信息信息信息息信息"
							},
							addressProvince: "甘肃",
							addressCity: "酒泉",
							commentInfo: {
								zhanfaNum: 50,
								pinglunNum: 60,
								dianzanNum: 50
							}
						}, {
							nickPick: "/static/userpic/14.jpg",
							nickName: "昵称",
							sex: 1, // 性别<>0 = 女  1 = 男
							age: 25,
							isGuanZhu: true,
							title: "动态内容动态内容动态内容动态内容动态内容动态内容",
							mediaType: "video", // 媒体类型<>image=图片&video=视频
							mediaSrc: "/static/datapic/15.jpg",
							videoInfo: {
								playNum: "50W",
								playTime: "2:45",
							},
							addressProvince: "甘肃",
							addressCity: "酒泉",
							commentInfo: {
								zhanfaNum: 50,
								pinglunNum: 60,
								dianzanNum: 50
							}
						},
						{
							nickPick: "/static/userpic/14.jpg",
							nickName: "昵称",
							sex: 0, // 性别<>0 = 女  1 = 男
							age: 25,
							isGuanZhu: false,
							title: "动态内容动态内容动态内容动态内容动态内容动态内容",
							mediaType: "image", // 媒体类型<>image=图片&video=视频
							mediaSrc: "/static/datapic/15.jpg",
							videoInfo: {
								playNum: "50W",
								playTime: "2:45",
							},
							addressProvince: "甘肃",
							addressCity: "酒泉",
							commentInfo: {
								zhanfaNum: 50,
								pinglunNum: 60,
								dianzanNum: 50
							}
						}
					]
				}, {
					loadMore: "正在加载更多",
					list: [{
							nickPick: "/static/userpic/14.jpg",
							nickName: "昵称",
							sex: 1, // 性别<>0 = 女  1 = 男
							age: 25,
							isGuanZhu: false,
							title: "动态内容动态内容动态内容动态内容动态内容动态内容",
							mediaType: "share", // 媒体类型<>image=图片&video=视频&share=分享
							mediaSrc: "/static/datapic/15.jpg",
							shareInfo: {
								text: "信息信息信息信息信息息信信息信息信息信信息信息息信息信息信息信息息信息信息信息信息信息信息息信信息信息信息信信息信息息信息信息信息信息息信息"
							},
							addressProvince: "甘肃",
							addressCity: "酒泉",
							commentInfo: {
								zhanfaNum: 50,
								pinglunNum: 60,
								dianzanNum: 50
							}
						}, {
							nickPick: "/static/userpic/14.jpg",
							nickName: "昵称",
							sex: 1, // 性别<>0 = 女  1 = 男
							age: 25,
							isGuanZhu: true,
							title: "动态内容动态内容动态内容动态内容动态内容动态内容",
							mediaType: "video", // 媒体类型<>image=图片&video=视频
							mediaSrc: "/static/datapic/15.jpg",
							videoInfo: {
								playNum: "50W",
								playTime: "2:45",
							},
							addressProvince: "甘肃",
							addressCity: "酒泉",
							commentInfo: {
								zhanfaNum: 50,
								pinglunNum: 60,
								dianzanNum: 50
							}
						},
						{
							nickPick: "/static/userpic/14.jpg",
							nickName: "昵称",
							sex: 0, // 性别<>0 = 女  1 = 男
							age: 25,
							isGuanZhu: false,
							title: "动态内容动态内容动态内容动态内容动态内容动态内容",
							mediaType: "image", // 媒体类型<>image=图片&video=视频
							mediaSrc: "/static/datapic/15.jpg",
							videoInfo: {
								playNum: "50W",
								playTime: "2:45",
							},
							addressProvince: "甘肃",
							addressCity: "酒泉",
							commentInfo: {
								zhanfaNum: 50,
								pinglunNum: 60,
								dianzanNum: 50
							}
						}
					]
				}]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(80) - uni.upx2px(60);
					this.windowHeight = height;
				}
			});
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
						nickPick: "/static/userpic/14.jpg",
						nickName: "昵称",
						sex: 1, // 性别<>0 = 女  1 = 男
						age: 25,
						isGuanZhu: true,
						title: "动态内容动态内容动态内容动态内容动态内容动态内容",
						mediaType: "video", // 媒体类型<>image=图片&video=视频
						mediaSrc: "/static/datapic/15.jpg",
						videoInfo: {
							playNum: "50W",
							playTime: "2:45",
						},
						addressProvince: "甘肃",
						addressCity: "酒泉",
						commentInfo: {
							zhanfaNum: 50,
							pinglunNum: 60,
							dianzanNum: 50
						}
					}

					this.tabBarScorllSpan[index].list.push(obj);
					this.tabBarScorllSpan[index].loadMore = '正在加载更多';
				}, 1000);
				// this.tabBarScorllSpan[index].loadMore = '没有数据啦';
			}
		},
		// 底部触底事件
		onReachBottom() {
			if (this.tabBarScorllSpan[this.tabSelectIndex].loadMore != '正在加载更多') {
				return;
			}
			this.tabBarScorllSpan[this.tabSelectIndex].loadMore = '加载中';

			// 模拟数据加载
			setTimeout(() => {
				var obj = {
					nickPick: "/static/userpic/14.jpg",
					nickName: "昵称",
					sex: 1, // 性别<>0 = 女  1 = 男
					age: 25,
					isGuanZhu: true,
					title: "动态内容动态内容动态内容动态内容动态内容动态内容",
					mediaType: "video", // 媒体类型<>image=图片&video=视频
					mediaSrc: "/static/datapic/15.jpg",
					videoInfo: {
						playNum: "50W",
						playTime: "2:45",
					},
					addressProvince: "甘肃",
					addressCity: "酒泉",
					commentInfo: {
						zhanfaNum: 50,
						pinglunNum: 60,
						dianzanNum: 50
					}
				}

				this.tabBarScorllSpan[this.tabSelectIndex].list.push(obj);
				this.tabBarScorllSpan[this.tabSelectIndex].loadMore = '正在加载更多';
			}, 1000);
			// this.tabBarScorllSpan[tabSelectIndex].loadMore = '没有数据啦';
		},
		// 下拉刷新
		onPullDownRefresh(){
			
			// 模拟加载数据
			console.log("加载数据");
			
			// 模拟数据加载
			setTimeout(() => {	
				uni.stopPullDownRefresh();
			}, 1000);
		}
	}
</script>

<style>
	.dynamic-navbar {
		width: 400upx;
		margin: 0 auto;
		margin-top: 30upx;
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
</style>
