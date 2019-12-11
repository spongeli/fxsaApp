<template>
	<view>
		<view class="chat-news" :class="{'chat-news-me':item.isMe}">
			<image :src="item.userpic" v-if="!item.isMe" mode="widthFix"></image>
			<view class="chat-news-detail" :class="{'chat-news-detail-me':item.isMe}">
				<view v-if="item.type == 'text'">{{item.text}}</view>
				<image :src="item.imgSrc" v-else-if="item.type == 'image'" mode="widthFix"></image>
			</view>
			<image :src="item.userpic" v-if="item.isMe" mode="widthFix"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			item: Object
		}
	}
</script>

<style>
	.chat-news {
		width: 720upx;
		margin: 0 auto;
		margin-top: 30upx;
		display: flex;
	}

	.chat-news>image {
		width: 100upx;
		border-radius: 50%;
	}

	.chat-news-detail {
		margin-left: 20upx;
		min-height: 60;
		line-height: 60upx;
		font-size: 40upx;
		max-width: 440upx;
		border-radius: 20upx;
		background-color: #F4F4F4;
		padding: 20upx;
	}

	.chat-news-detail>image {
			max-width: 350upx;
			max-height: 400upx;
	}

	.chat-news-me {
		justify-content: flex-end;
	}

	.chat-news-detail-me {
		margin-right: 20upx;
	}
</style>
