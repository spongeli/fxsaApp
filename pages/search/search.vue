<template>
	<view>
		<block v-for="(item,index) in dataList" :key="index">
			<index-list :item="item"></index-list>
		</block>
		<template v-if="dataList.length>0">
			<load-more :loadMore="loadMoreText"></load-more>
		</template>
		<template v-else-if="isloadData && dataList.length == 0">
			<no-thing></no-thing>
		</template>
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list/index-list.vue";
	import loadMore from "../../components/common/load-more.vue";
	import noThing from "../../components/common/no-thing.vue"
	export default {
		components: {
			indexList,
			loadMore,
			noThing
		},
		data() {
			return {
				isloadData: false,
				searchText: "",
				loadMoreText: "正在加载更多",
				dataList: []
			}
		},
		// 监听取消按钮
		onNavigationBarButtonTap(e) {
			if (e.index == 0) {
				uni.navigateBack({
					delta: 1
				});
			}
		},
		// 监听搜索框输入事件
		onNavigationBarSearchInputChanged(e) {
			// console.log("监听搜索框输入事件:" + e.text);
		},
		// 监听确认事件
		onNavigationBarSearchInputConfirmed(e) {
			// console.log("监听确认事件:" + e.text);
			this.searchText = e.text;
			this.getData();
		},
		onReachBottom() {
			if (this.loadMoreText != '正在加载更多') {
				return;
			}
			this.loadMoreText = '加载中';

			// 模拟数据加载
			setTimeout(() => {
				var obj = {
					userPic: "/static/userpic/1.jpg",
					userNick: "昵称",
					isGuanzhu: false,
					title: "发表内容发表内容发表内容发表内容发表内容",
					messageType: "img", // img:图片   video:视屏
					messageSrc: "/static/datapic/11.jpg",
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

				this.dataList.push(obj);
				this.loadMoreText = '正在加载更多';
			}, 1000);
			// this.loadMoreText = '没有数据啦';
		},
		onLoad() {
			uni.startPullDownRefresh();
		},
		onPullDownRefresh() {
			this.getData();
		},
		methods: {
			getData() {
				setTimeout(() => {
					let arr = [{
						userPic: "/static/userpic/1.jpg",
						userNick: "昵称",
						isGuanzhu: false,
						title: "发表内容发表内容发表内容发表内容发表内容",
						messageType: "video", // img:图片   video:视屏
						messageSrc: "/static/datapic/11.jpg",
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
						userPic: "/static/userpic/1.jpg",
						userNick: "昵称",
						isGuanzhu: false,
						title: "发表内容发表内容发表内容发表内容发表内容",
						messageType: "img", // img:图片   video:视屏
						messageSrc: "/static/datapic/11.jpg",
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
						userPic: "/static/userpic/1.jpg",
						userNick: "昵称",
						isGuanzhu: true,
						title: "发表内容发表内容发表内容发表内容发表内容",
						messageType: "img", // img:图片   video:视屏
						messageSrc: "/static/datapic/11.jpg",
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
					this.dataList = arr;
					this.searchText = '';
					this.isloadData = true;
					uni.stopPullDownRefresh();
				}, 1000);
			}
		}

	}
</script>

<style>

</style>
