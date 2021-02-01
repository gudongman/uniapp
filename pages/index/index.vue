<template>
	<view class="wrap">
		<u-divider border-color="#84cdf4" half-width="50">u-line-2</u-divider>
		<view class="u-line-2">
			是日也，天朗气清，惠风和畅，仰观宇宙之大，俯察品类之盛，所以游目骋怀，足以极视听之娱，信可乐也
			是日也，天朗气清，惠风和畅，仰观宇宙之大，俯察品类之盛，所以游目骋怀，足以极视听之娱，信可乐也
			是日也，天朗气清，惠风和畅，仰观宇宙之大，俯察品类之盛，所以游目骋怀，足以极视听之娱，信可乐也
		</view>
		<u-divider>照片</u-divider>
		<u-image width="50px" height="50px" :src="src"></u-image>
		<u-divider>按钮 custom-style绑定样式</u-divider>
		<u-button plain shape="circle" type="primary" ripple style="width: 100px;">测试</u-button>
		<u-button type="info" :custom-style="customStyle"> 11</u-button>
		<!-- <u-row gutter="16">
			<u-col :span="3" class="demo-layout bg-purple"></u-col>
			<u-col :span="9" class="demo-layout bg-purple-light"></u-col>
		</u-row> -->
		<u-divider>布局  gutter=2 两个块间隔的距离是2upx</u-divider>
		<u-divider>span和为12 offset偏移的栏数 justify='end'等</u-divider>
		<view class="wrap">
			<!-- gutter 两个块间隔的距离是2upx -->
			<u-row  justify="between">
				<u-col span="3">
					<view class="demo-layout bg-purple"></view>
				</u-col>
				<u-col span="4">
					<view class="demo-layout bg-purple-light"></view>
				</u-col>
				<u-col span="3">
					<view class="demo-layout bg-purple-dark"></view>
				</u-col>
			</u-row>
			<u-row gutter="16">
				<u-col span="3">
					<view class="demo-layout bg-purple"></view>
				</u-col>
				<u-col span="3" offset="6">
					<view class="demo-layout bg-purple-light"></view>
				</u-col>
			</u-row>
		</view>
		
		<u-divider>Cell 单元格 icon title value</u-divider>
		<u-divider>u-cell-group title-style定义样式</u-divider>
		<u-cell-group title="分组标题" :border="false" :title-style="{fontSize: '34upx'}" >
			<u-cell-item icon="setting-fill" title="个人设置"  :index="1" @click="alert" label="描述信息" arrow-direction="down"></u-cell-item>
			<u-cell-item icon="integral-fill" title="会员等级" value="新版本"></u-cell-item>
		</u-cell-group>
		<u-cell-group>
			<u-cell-item title="测试" arrow-direction="down">
				<u-icon slot></u-icon>
			</u-cell-item>
		</u-cell-group>

		<u-divider>badge 徽标</u-divider>
		<view class="view2" style="position: relative">
			<u-badge type="error" count="19" :overflow-count="9" :offset="[-10,-10]" size="mini"></u-badge>
			<!-- :is-dot="true" -->
		</view>
		<u-divider>tag 标签 mode="light/dark/plain"</u-divider>
		<u-tag type="success" text="测试" shape="circle" mode="light" bg-color="#f4f4f4" color="grey" border-color="grey" closeable @close="close()" :show="show"></u-tag>
		
		<!-- m -->
		<!-- <u-badge type="error" count="7"></u-badge> -->

	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: 'https://cdn.uviewui.com/uview/example/fade.jpg',
				customStyle: {marginTop: '10upx', width: '100upx'},
				
				show: true
			}
		},
		onLoad() {

		},
		methods: {
			alert(index){
				console.log(index);
			},
			close(){
				this.show = false
			},
		
		}
	}
</script>

<style lang="scss" scoped>
	.view2{
		width: 100upx;
		height: 100upx;
		background-color: #f4f4f4;
		position: relative;
	}
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
