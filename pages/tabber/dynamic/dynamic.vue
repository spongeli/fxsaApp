<template>
	<view class="body">

		<!-- 自定义导航栏 -->
		<news-nav-bar :tabBers="tabBers" :tabBerIndex="tabBerIndex" @changtabIndex="changtabIndex"></news-nav-bar>

		<!-- swiper 面板 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:windowHeight + 'px'}" :current="tabBerIndex" @change="changSwiper">

				<!-- 关注 -->
				<swiper-item>
					<scroll-view class="list" scroll-y="true" show-scrollbar="true" @scrolltolower="scrollDynamicPull">
						<!-- 动态内容 -->
						<block v-for="(item,index) in dynamicItem.dynamicList" :key="index">
							<dynamic-list :item="item"></dynamic-list>
						</block>
						<!-- 加载更多 -->
						<load-more :loadMore="dynamicItem.loadMore"></load-more>
					</scroll-view>
				</swiper-item>

				<!-- 话题 -->
				<swiper-item>
					<scroll-view class="list" scroll-y="true" show-scrollbar="false">
						<!-- 搜索 -->
						<view class="scroll-input">
							<input class="uni-input" placeholder="搜索内容" placeholder-class="icon iconfont icon-sousuo scroll-input-placeholder" />
						</view>
						<!-- 轮播图 -->
						<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
							<block v-for="(item,index) in bannerList" :key="index">
								<swiper-item>
									<image :src="item.src" mode="widthFix" lazy-load></image>
								</swiper-item>
							</block>
						</swiper>
						<!-- 热门分类 -->
						<view class="hots">
							<view class="v-fjs">
								<view>热门分类</view>
								<view class="v-fjc">更多<view class="icon iconfont icon-jinru"></view>
								</view>
							</view>
							<view class="v-fjs">
								<block v-for="(item,index) in hotsBars" :key="index">
									<view>{{item.name}}</view>
								</block>
							</view>
						</view>
						<!-- 最近更新 -->
						<newest-update :newestList="newestList"></newest-update>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import newsNavBar from "../../../components/common/news-nav-bar.vue"
	import dynamicList from "../../../components/dynamic/dynamic-list.vue";
	import loadMore from "../../../components/common/load-more.vue";
	import newestUpdate from "../../../components/common/newest-update.vue"
	export default {
		components: {
			dynamicList,
			newsNavBar,
			loadMore,
			newestUpdate
		},
		data() {
			return {
				windowHeight: 0,
				tabBerIndex: 0,
				tabBers: [{
					name: "关注",
					id: "guanzhu"
				}, {
					name: "话题",
					id: "huati"
				}],
				dynamicItem: {
					loadMore: "正在加载更多",
					// 动态信息
					dynamicList: [{
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
				},
				bannerList: [{
					src: "../../../static/banner1.jpg"
				}, {
					src: "../../../static/banner1.jpg"
				}, {
					src: "../../../static/banner1.jpg"
				}],
				hotsBars: [{
						name: "最新"
					},
					{
						name: "游戏"
					}, {
						name: "情感"
					},
					{
						name: "打卡"
					},
					{
						name: "故事"
					},
					{
						name: "最新"
					}
				],
				newestList:[{
					src:"/static/topicpic/13.jpeg",
					contextHeader:"#淘宝记录薄#",
					contextTitle:"120斤到85斤 我的人生反转",
					contextFooter:"动态 545 今日 720"
				},{
					src:"/static/topicpic/13.jpeg",
					contextHeader:"#淘宝记录薄#",
					contextTitle:"120斤到85斤 我的人生反转",
					contextFooter:"动态 545 今日 720"
				},{
					src:"/static/topicpic/13.jpeg",
					contextHeader:"#淘宝记录薄#",
					contextTitle:"120斤到85斤 我的人生反转",
					contextFooter:"动态 545 今日 720"
				},{
					src:"/static/topicpic/13.jpeg",
					contextHeader:"#淘宝记录薄#",
					contextTitle:"120斤到85斤 我的人生反转",
					contextFooter:"动态 545 今日 720"
				}]
			}
		},
		methods: {
			// 切换话题
			changtabIndex(index) {
				this.tabBerIndex = index;
			},
			changSwiper(e) {
				this.tabBerIndex = e.target.current;
			},
			// 下拉触底
			scrollDynamicPull() {
				if (this.dynamicItem.loadMore != '正在加载更多') {
					return;
				}
				this.dynamicItem.loadMore = '加载中';

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

					this.dynamicItem.dynamicList.push(obj);
					this.dynamicItem.loadMore = '正在加载更多';
				}, 1000);
				// this.dynamicItem.loadMore = '没有数据啦';
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(80);
					this.windowHeight = height;
				}
			});
		}
	}
</script>

<style>
	/* 搜索框 */
	.scroll-input {
		border-top: 5upx solid #EEEEEE;
		width: 100%;
		padding: 10upx 15upx 10upx 15upx;
	}

	.uni-input {
		background-color: #F4F4F4;
		border-radius: 15upx;
		width: 90%;
	}

	.scroll-input-placeholder {
		display: flex;
		justify-content: center;
		font-size: 30upx;
	}

	/* 轮播图 */
	.topic-swiper {
		padding: 0 20upx 20upx 20upx;
	}

	.topic-swiper image {
		width: 100%;
		border-radius: 10upx;
	}

	/* 热门分类 */
	.hots {
		width: 97%;
		padding: 20upx 25upx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		border-top: 5upx solid #EEEEEE;
		border-bottom: 5upx solid #EEEEEE;
	}

	.hots>view:first-child>view:first-child{
		font-size: 30upx;
	}
	.hots>view:first-child>view:last-child {
		margin-right: 20upx;
		color: #A1A1A1;
	}

	.hots>view:last-child {
		margin-top: 20upx;
	}

	.hots>view:last-child>view {
		padding: 5upx 15upx;
		background-color: #F7F7F7;
		color: #A1A1A1;
		border-radius: 10upx;
	}

	.hots>view:last-child>view:last-child {
		margin-right: 20upx;
	}
</style>
