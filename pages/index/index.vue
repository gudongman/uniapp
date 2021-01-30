<template>
	<view class="wrap">
		<view class="u-line-2">
			是日也，天朗气清，惠风和畅，仰观宇宙之大，俯察品类之盛，所以游目骋怀，足以极视听之娱，信可乐也
			是日也，天朗气清，惠风和畅，仰观宇宙之大，俯察品类之盛，所以游目骋怀，足以极视听之娱，信可乐也
			是日也，天朗气清，惠风和畅，仰观宇宙之大，俯察品类之盛，所以游目骋怀，足以极视听之娱，信可乐也
		</view>
		<u-image width="50px" height="50px" :src="src"></u-image>
		<u-button plain shape="circle" type="primary" ripple style="width: 100px;">测试</u-button>
		<!-- <u-row gutter="16">
			<u-col :span="3" class="demo-layout bg-purple"></u-col>
			<u-col :span="9" class="demo-layout bg-purple-light"></u-col>
		</u-row> -->
		
		<view class="wrap">
				<u-row gutter="16">
					<u-col span="3">
						<view class="demo-layout bg-purple"></view>
					</u-col>
					<u-col span="4">
						<view class="demo-layout bg-purple-light"></view>
					</u-col>
					<u-col span="5">
						<view class="demo-layout bg-purple-dark"></view>
					</u-col>
				</u-row>
				<u-row gutter="16" justify="space-between">
					<u-col span="3">
						<view class="demo-layout bg-purple"></view>
					</u-col>
					<u-col span="9">
						<view class="demo-layout bg-purple-light"></view>
					</u-col>
				</u-row>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: 'https://cdn.uviewui.com/uview/example/fade.jpg'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	.wrap {
			padding: 24rpx;
		}
	
		.u-row {
			margin: 40rpx 0;
		}
	
		.demo-layout {
			height: 80rpx;
			border-radius: 8rpx;
		}
	
		.bg-purple {
			background: #d3dce6;
		}
	
		.bg-purple-light {
			background: #e5e9f2;
		}
	
		.bg-purple-dark {
			background: #99a9bf;
		}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

</style>
