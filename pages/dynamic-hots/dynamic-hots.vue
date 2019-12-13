<template>
	<view>
		<!-- 导航 -->
		<index-scroll :tabBars="tabBars" :tabSelectIndex="tabSelectIndex" @changScrollTab="changScrollTab"></index-scroll>

		<!-- swiper 面板 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:windowHeight + 'px'}" :current="tabSelectIndex" @change="changSwiper">
				<swiper-item v-for="(items,indexs) in tabBarScorllSpan" :key="indexs">
					<scroll-view class="list" scroll-y="true" show-scrollbar="false" @scrolltolower="scrollPull(indexs)">
						<template v-if="items.list.length>0">
							<!-- 列表 -->
							<block v-for="(item,index) in items.list" :key="index">
								<newest-update :item="item"></newest-update>
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
	import indexScroll from "../../components/index/index-scroll/index-scroll.vue";
	import noThing from "../../components/common/no-thing.vue";
	import newestUpdate from "../../components/common/newest-update.vue";
	import loadMore from "../../components/common/load-more.vue"
	export default {
		components: {
			indexScroll,
			noThing,
			newestUpdate,
			loadMore
		},
		data() {
			return {
				windowHeight: 0,
				tabSelectIndex: 0,
				tabBarScorllSpan: [{
						loadMore: "正在加载更多",
						list: [{
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
						}, {
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 720"
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
				],
				dynamicHotList: [{
					src: "/static/topicpic/13.jpeg",
					contextHeader: "#淘宝记录薄#",
					contextTitle: "120斤到85斤 我的人生反转",
					contextFooter: "动态 545 今日 720"
				}, {
					src: "/static/topicpic/13.jpeg",
					contextHeader: "#淘宝记录薄#",
					contextTitle: "120斤到85斤 我的人生反转",
					contextFooter: "动态 545 今日 720"
				}, {
					src: "/static/topicpic/13.jpeg",
					contextHeader: "#淘宝记录薄#",
					contextTitle: "120斤到85斤 我的人生反转",
					contextFooter: "动态 545 今日 720"
				}, {
					src: "/static/topicpic/13.jpeg",
					contextHeader: "#淘宝记录薄#",
					contextTitle: "120斤到85斤 我的人生反转",
					contextFooter: "动态 545 今日 720"
				}]
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
							src: "/static/topicpic/13.jpeg",
							contextHeader: "#淘宝记录薄#",
							contextTitle: "120斤到85斤 我的人生反转",
							contextFooter: "动态 545 今日 999"
						}

					this.tabBarScorllSpan[index].list.push(obj);
					this.tabBarScorllSpan[index].loadMore = '正在加载更多';
				}, 1000);
				// this.tabBarScorllSpan[index].loadMore = '没有数据啦';
			},
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

</style>
