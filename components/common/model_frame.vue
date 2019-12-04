<template>
	<view v-if="show" class="modal_frame_background">
		<view class="modal_frame_content" :class="postion">
			<slot />
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			postion: {
				type: String,
				default: "center"
			},
			show:{
				type: Boolean,
				default: true
			}
		}
	}
</script>

<style>
	.modal_frame_background {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		left: 0;
		background-color: rgba(53, 53, 53, 0.85);
	}

	.modal_frame_content {
		height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.center {
		justify-content: center;
	}

	.top {
		justify-content: flex-start;
	}

	.end {
		justify-content: flex-end;
	}
</style>
