<template>
	<view>
		搜索页
	</view>
</template>

<script>
	export default {
		data() {
			return {

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
			console.log("监听搜索框输入事件:" + e.text);
		},
		// 监听确认事件
		onNavigationBarSearchInputConfirmed(e) {
			console.log("监听确认事件:" + e.text);
		},
		methods: {

		}
	}
</script>

<style>

</style>
