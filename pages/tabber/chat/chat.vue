<template>
	<view class="body">
		<!-- 自定义导航 -->
		<text-uni-nav-bar centerText="小纸条" @leftClick="leftClick" @rightClick="rightClick"></text-uni-nav-bar>

		<!-- 聊天列表 -->
		<block v-for="(item,index) in chatLists" :key="index">
			<chat-list :chatInfo="item"></chat-list>
		</block>

		<!-- 加载跟多 -->
		<load-more :loadMore="loadMoreMsg"></load-more>

		<!-- 右边小提示 -->
		<chat-tips :show="tipsShow" @addUser="addUser" @deleteUnReader="deleteUnReader" @cancel="cancel"></chat-tips>
	</view>
</template>

<script>
	import textUniNavBar from "../../../components/common/text-uni-nav-bar.vue"
	import chatList from "../../../components/common/chat-list.vue";
	import chatTips from "../../../components/chat/chat-tips.vue";
	import loadMore from "../../../components/common/load-more.vue";
	export default {
		components: {
			textUniNavBar,
			chatList,
			chatTips,
			loadMore
		},
		data() {
			return {
				loadMoreMsg: "正在加载更多",
				tipsShow: false,
				chatLists: [{
					userpic: "/static/userpic/6.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 12
				}, {
					userpic: "/static/userpic/7.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 0
				}, {
					userpic: "/static/userpic/8.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 12
				}, {
					userpic: "/static/userpic/9.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 0
				}, {
					userpic: "/static/userpic/8.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 0
				}, {
					userpic: "/static/userpic/9.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 2
				}, {
					userpic: "/static/userpic/8.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 12
				}, {
					userpic: "/static/userpic/9.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 2
				}, {
					userpic: "/static/userpic/8.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 12
				}, {
					userpic: "/static/userpic/9.jpg",
					usernick: "JIA一勺",
					chatTime: "13:58",
					chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
					unReaderNum: 2
				}]
			}
		},
		onPullDownRefresh() {
			this.pullRefresh();
		},
		onReachBottom() {
			this.loadMore();
		},
		methods: {
			cancel() {
				this.tipsShow = false;
			},
			addUser() {
				this.cancel();
				console.log("addUser");
			},
			deleteUnReader() {
				this.cancel();
				console.log("deleteUnReader");
			},
			rightClick() {
				this.tipsShow = true;
			},
			leftClick() {
				uni.navigateTo({
					url: "../../follow/follow",
					animationType: 'pop-in',
					animationDuration: 200
				})
			},
			pullRefresh() {
				setTimeout(() => {
					let chatArray = [{
						userpic: "/static/userpic/7.jpg",
						usernick: "JIA一勺1111",
						chatTime: "13:58",
						chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
						unReaderNum: 0
					}];
					this.chatLists = chatArray;
					uni.stopPullDownRefresh();
				}, 1000);
			},
			loadMore() {
				if (this.loadMoreMsg != '正在加载更多') {
					return;
				}
				this.loadMoreMsg = '加载中';

				// 模拟数据加载
				setTimeout(() => {
					var obj = {
						userpic: "/static/userpic/7.jpg",
						usernick: "JIA一勺1111",
						chatTime: "13:58",
						chatText: "赵丽颖《知否》一句话打脸，读书读书读书读书",
						unReaderNum: 0
					}

					this.chatLists.push(obj);
					this.loadMoreMsg = '正在加载更多';
				}, 1000);
			}
		},
	}
</script>

<style>
	.body {
		width: 750upx;
	}
</style>
