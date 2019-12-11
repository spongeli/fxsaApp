<template>
	<view>
		<!-- 导航栏 -->
		<text-uni-nav-bar leftIcon="icon-fanhui" rightIcon="icon-geren" :centerText="chatDetailInfo.userNickName" @leftClick="leftClick"
		 @rightClick="rightClick"></text-uni-nav-bar>

		<!-- 聊天界面 -->
		<block v-for="(item,index) in chatList" :key="index">
			<chat-list :item="item"></chat-list>
		</block>

		<!-- 底部输入框 -->
		<chat-input @submit="submit"></chat-input>
	</view>
</template>

<script>
	import textUniNavBar from "../../components/common/text-uni-nav-bar.vue";
	import chatInput from "../../components/chat/chat-input.vue";
	import chatList from "../../components/chat/chat-list.vue";
	export default {
		components: {
			textUniNavBar,
			chatInput,
			chatList
		},
		data() {
			return {
				chatDetailInfo: {
					userNickName: "JAVA大亨"
				},
				chatList: [{
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学习",
					messageTime: "1555146412"
				},{
					isMe: false,
					userpic: "/static/userpic/10.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学习",
					messageTime: "1555146412"
				},{
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "text", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学习",
					messageTime: "1555146412"
				},{
					isMe: false,
					userpic: "/static/userpic/10.jpg",
					type: "text", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/userpic/10.jpg",
					text: "学习学习学学习学习学习学习学习学习学习学习学习学习学习学习学习学习学习习",
					messageTime: "1555146412"
				},{
					isMe: true,
					userpic: "/static/userpic/10.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/1.jpg",
					text: "学习学习学习",
					messageTime: "1555146412"
				},{
					isMe: false,
					userpic: "/static/userpic/10.jpg",
					type: "image", // 消息记录类型<>text=文字&image=图片&video=视频
					imgSrc: "/static/1.jpg",
					text: "学习学习学学习学习学习学习学习学习学习学习学习学习学习学习学习学习学习习",
					messageTime: "1555146412"
				}]
			}
		},
		methods: {
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
				console.log("发送的消息是：" + obj);
			}
		}
	}
</script>

<style>

</style>
