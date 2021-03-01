<template>
	<view class="">
		<u-dropdown :close-on-click-mask="true" ref="uDropdown" activeColor="#2979ff" :borderBottom="true">
			<u-dropdown-item @change="change" v-model="value1" title="距离" :options="options1"></u-dropdown-item>
			<u-dropdown-item @change="change" v-model="value2" title="温度" :options="options2"></u-dropdown-item>
			<u-dropdown-item title="属性">
				<view class="slot-content">
					<view class="item-box">
						<view class="item" :class="[item.active ? 'active' : '']" @tap="tagClick(index)" v-for="(item, index) in list" :key="index">
							{{item.label}}
						</view>
					</view>
					<u-button type="primary" @click="closeDropdown">确定</u-button>
				</view>
			</u-dropdown-item>
		</u-dropdown>
		
		{{this.list.map(item=>{ if(item.active){ return item } })}}
		
		<u-tabs :list="list2" :is-scroll="false" :current="current" @change="change2"></u-tabs>
		
		<u-subsection :list="list2" :current="current2"  @change="sectionChange"></u-subsection>
		
			<u-upload :action="action" :file-list="fileList" :max-count="2"></u-upload>
			
			<u-steps :list="numList" :current="1" active-color="#6b3aff" mode="number"></u-steps>
			<u-circle-progress active-color="#6b3aff" :percent="100" duration="2000" width="300" border-width="20">
				<view class="">
					查找中
				</view>
			</u-circle-progress>
			<u-line-progress active-color="#2979ff" :percent="70"></u-line-progress>
			<u-count-down :timestamp="timestamp" separator="zh"></u-count-down>
			<u-alert-tips :show="show" type="warning" :title="title" :description="description" show-icon close-able @close="closeTip" ></u-alert-tips>
			<u-button @click="showToast">toast消息提示</u-button>
			<u-toast ref="uToast" />
			<u-notice-bar mode="vertical"  :volume-icon="false"   :is-circular="true" :list="noticelist"></u-notice-bar>
			<u-top-tips ref="uTips" duration="2000"></u-top-tips>
	
			<u-swipe-action :show="item.show" :index="index" 
				v-for="(item, index) in swipelist" :key="item.id" 
				@click="click" @open="open"
				:options="options"
			>
				<view class="item u-border-bottom">
					<image mode="aspectFill" :src="item.images" />
					<!-- 此层wrap在此为必写的，否则可能会出现标题定位错误 -->
					<view class="title-wrap">
						<text class="title u-line-2">{{ item.title }}</text>
					</view>
				</view>
			</u-swipe-action>
			<u-modal ref="uModal" v-model="modalshow" content="测试" @confirm="confirm" :async-close="true"></u-modal>
				<u-button @click="showModal">弹起异步Modal</u-button>
				<br>
				<u-line color="grey" />
				<!-- <u-mask :show="true" @click="show = false"></u-mask> -->
				<br>
				<u-grid :col="2">
					<u-grid-item>
						<u-badge count="9"></u-badge>
						<u-icon name="photo" :size="46"></u-icon>
						<view class="grid-text">图片</view>
					</u-grid-item>
					<u-grid-item>
						<!-- <image src="/static/image/icon/hot5.png" class="badge-icon"></image> -->
						<u-icon name="lock" :size="46"></u-icon>
						<view class="grid-text">锁头</view>
					</u-grid-item>
				</u-grid>
				时间轴
	</view>
</template>

<script>
	export default {
		data(){
			return {
				modalshow: false,
				swipelist: [
					{
						id: 1,
						title: '长安回望绣成堆，山顶千门次第开，一骑红尘妃子笑，无人知是荔枝来',
						images: 'https://cdn.uviewui.com/uview/common/logo.png',
						show: false
					},
					{
						id: 2,
						title: '新丰绿树起黄埃，数骑渔阳探使回，霓裳一曲千峰上，舞破中原始下来',
						images: 'https://cdn.uviewui.com/uview/common/logo.png',
						show: false
					},
					{
						id: 3,
						title: '登临送目，正故国晚秋，天气初肃。千里澄江似练，翠峰如簇',
						images: 'https://cdn.uviewui.com/uview/common/logo.png',
						show: false,
					}
				],
				disabled: false,
				btnWidth: 180,
				show: false,
				options: [
					{
						text: '收藏',
						style: {
							backgroundColor: '#007aff'
						}
					},
					{
						text: '删除',
						style: {
							backgroundColor: '#dd524d'
						}
					}
				],
				noticelist: [
									'寒雨连江夜入吴',
									'平明送客楚山孤',
									'洛阳亲友如相问',
									'一片冰心在玉壶'
								],
				show: true,
				title: '登高望远',
				description: '欲穷千里目，更上一层楼',
				timestamp: 60,
				numList: [{
									name: '下单'
								}, {
									name: '出库'
								}, {
									name: '运输'
								}, {
									name: '签收'
								}, ],
				// 演示地址，请勿直接使用
				action: 'http://www.example.com/upload',
				fileList: [
					{
						url: 'http://pics.sc.chinaz.com/files/pic/pic9/201912/hpic1886.jpg',
					}
				],
				list2: [{
					name: '待收货'
				}, {
					name: '待付款'
				}, {
					name: '待评价',
					count: 5
				}],
				current: 0,
				current2: 0,
				value: 1,
				
				value1: 1,
				value2: 2,
				options1: [{
						label: '默认排序',
						value: 1,
					},
					{
						label: '距离优先',
						value: 2,
					},
					{
						label: '价格优先',
						value: 3,
					}
				],
				options2: [{
						label: '去冰',
						value: 1,
					},
					{
						label: '加冰',
						value: 2,
					},
				],
				list: [{
						label: '琪花瑶草',
						active: true,
					},
					{
						label: '清词丽句',
						active: false,
					},
					{
						label: '宛转蛾眉',
						active: false,
					}
				],
			}
		},
		onReady() {
					this.$refs.uTips.show({
						title: '铁马冰河入梦来',
						type: 'success',
						duration: '2300'
					})
				},
		methods:{
			confirm(){
				setTimeout(()=>{
					this.modalshow = false
					// this.$refs.uModal.clearLoading();
				},1000)
			},
			showModal(){
				this.modalshow= true;
			},
			click(index1, index){
				// 第一个参数为通过Props传入的index参数，第二个参数为滑动按钮的索引，
				if(index==1){
					this.swipelist.splice(index,1)
					this.$u.toast(`删除了第${index}个cell`)
				}else{
					this.$u.toast(`收藏成功`)
				}
			},
			open(index){
				// 先将正在被操作的swipeAction标记为打开状态，否则由于props的特性限制，
				// 原本为'false'，再次设置为'false'会无效
				this.swipelist[index].show=true
				this.swipelist.map((item,idx)=>{
					if(index!=idx){item.show= false};
					return item
				})
			},
			showToast() {
				this.$refs.uToast.show({
					title: '登录成功',
					type: 'success',
					// url: '/pages/index/index' //跳回的地址
					callback : ()=>{
						console.log('toast显示完毕')
					}
				})
			},
			closeTip(){
				this.show= false
			},
			sectionChange(index){
				this.current2 = index;
				this.$u.toast(`点击了第${index}项`);
			},
	 		change2(index) {
				this.current = index;
			},
			tagClick(index) {
				this.list[index].active = !this.list[index].active;
			},
			valChange(e){
				console.log('步进器的值',e.value);
			},
			change(index) {
				this.$u.toast(`点击了第${index}项`);
			},
			closeDropdown() {
				
				this.$refs.uDropdown.close();
			}
		},
		}
</script>

<style lang="scss" scoped>
	.item {
			display: flex;
			padding: 20rpx;
		}
		
		image {
			width: 120rpx;
			flex: 0 0 120rpx;
			height: 120rpx;
			margin-right: 20rpx;
			border-radius: 12rpx;
		}
		
		.title {
			text-align: left;
			font-size: 28rpx;
			color: $u-content-color;
			margin-top: 20rpx;
		}
	.slot-content{
		background-color: #FFFFFF;
		padding: 24rpx;
	}
	.item-box {
		margin-bottom: 50rpx;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		
		.item {
			border: 1px solid $u-type-primary;
			color: $u-type-primary;
			padding: 8rpx 40rpx;
			border-radius: 100rpx;
			margin-top: 30rpx;
		}
		
		.active {
			color: #FFFFFF;
			background-color: $u-type-primary;
		}
	}
</style>
