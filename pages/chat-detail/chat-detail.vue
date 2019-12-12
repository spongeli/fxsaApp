<template>
	<view>
		<!-- 导航栏 -->
		<text-uni-nav-bar leftIcon="icon-fanhui" rightIcon="icon-geren" :centerText="chatDetailInfo.userNickName" @leftClick="leftClick"
		 @rightClick="rightClick"></text-uni-nav-bar>


		<scroll-view scroll-y="true" :scroll-top="scrollTop" scroll-with-animation="true" :style="{height:scrollStyle.contentH + 'px'}">
			<!-- 聊天界面 -->
			<block v-for="(item,index) in chatList" :key="index">
				<view class="scroll-list-item">
					<chat-list :item="item"></chat-list>
				</view>
			</block>
		</scroll-view>
		<!-- 底部输入框 -->
		<chat-input @submit="submit"></chat-input>
	</view>
</template>

<script>
	import textUniNavBar from "../../components/common/text-uni-nav-bar.vue";
	import chatInput from "../../components/chat/chat-input.vue";
	import chatList from "../../components/chat/chat-list.vue";
	import time from "../../common/time.js";
	export default {
		components: {
			textUniNavBar,
			chatInput,
			chatList
		},
		data() {
			return {
				scrollTop: 0,
				scrollStyle: {
					contentH: 0,
					itemH: 0
				},
				chatDetailInfo: {
					userNickName: "JAVA大亨"
				},
				chatList: []
			}
		},
		onReady() {
			this.innitSystem();
			this.getData();
			this.scrollToBottom(true);
		},
		methods: {
			scrollToBottom(isFirst = false) {
				let query = uni.createSelectorQuery().in(this);
				let items = query.selectAll(".scroll-list-item");
				//将回调延迟到下次 DOM 更新循环之后执行。在修改数据之后立即使用它，然后等待 DOM 更新。它跟全局方法 Vue.nextTick 一样，不同的是回调的 this 自动绑定到调用它的实例上。 
				this.$nextTick(() => {
					items.fields({
						size: true
					}, data => {
						if (data) {
							if (isFirst) {
								for (var i = 0; i < data.length; i++) {
									this.scrollStyle.itemH += data[i].height;
								}
							} else {
								this.scrollStyle.itemH += data[data.length - 1].height;
							}
							this.scrollTop = (this.scrollStyle.itemH > this.scrollStyle.contentH) ? this.scrollStyle.itemH : 0;
						}
					}).exec();
				});
			},
			getData() {
				let arr = [{
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学习",
					messageTime: "1555146412"
				}, {
					isMe: false,
					userpic: "/static/userpic/11.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学习",
					messageTime: "1555146412"
				}, {
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "text", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学习",
					messageTime: "1576121580"
				}, {
					isMe: false,
					userpic: "/static/userpic/11.jpg",
					type: "text", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学学习学习学习学习学习学习学习学习学习学习学习学习学习学习学习习",
					messageTime: "1576118251"
				}, {
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/1.jpg",
					text: "学习学习学习",
					messageTime: "1576121971"
				}, {
					isMe: false,
					userpic: "/static/userpic/11.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/1.jpg",
					text: "学习学习学学习学习学习学习学习学习学习学习学习学习学习学习学习学习学习习",
					messageTime: "1576121851"
				}];
				for (var i = 0; i < arr.length; i++) {
					arr[i].getTimeMsg = time.gettime.getChatTime(arr[i].messageTime, i > 0 ? arr[i - 1].messageTime : 0);
				};
				this.chatList = arr;
			},
			innitSystem() {
				uni.getSystemInfo({
					success: (res) => {
						this.scrollStyle.contentH = res.windowHeight - uni.upx2px(210);
					}
				});
			},
			leftClick() {
				uni.navigateBack({
					delta: 1,
					animationType: 'pop-out',
					animationDuration: 200
				})
			},
			rightClick() {
				uni.navigateTo({
					url: "../user-info/user-info"
				});
			},
			// 发送消息
			submit(obj) {
				let now = new Date().getTime();
				var obj = {
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "text", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: obj,
					messageTime: now,
					getTimeMsg: time.gettime.getChatTime(now, this.chatList[this.chatList.length - 1].messageTime)
				}
				this.chatList.push(obj);
				this.scrollToBottom();
			}
		}
	}
</script>

<style>

</style>
