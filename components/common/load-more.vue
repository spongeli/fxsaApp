<template>
	<view class="load_more">{{loadMore}}</view>
</template>

<script>
	export default {
		props:{
			loadMore:String
		}
	}
</script>

<style>
	.load_more{
		text-align: center;
		color: #AAAAAA;
		padding: 10upx 0;
	}
</style>
