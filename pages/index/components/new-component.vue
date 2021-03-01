<template>
	<view class="">
		<u-number-box input-width="100" :input-height="40" v-model="value" @change="valChange" :max="10" :min="0" :step="2"></u-number-box>
		
		
		
		<u-dropdown :close-on-click-mask="true" ref="uDropdown" activeColor="#2979ff" :borderBottom="true">
			<u-dropdown-item @change="change" v-model="value1" title="距离" :options="options1"></u-dropdown-item>
			<u-dropdown-item @change="change" v-model="value2" title="温度" :options="options2"></u-dropdown-item>
			<!-- <u-dropdown-item title="属性">
				<view class="slot-content">
					<view class="item-box">
						<view class="item" :class="[item.active ? 'active' : '']" @tap="tagClick(index)" v-for="(item, index) in list" :key="index">
							{{item.label}}
						</view>
					</view>
					<u-button type="primary" @click="closeDropdown">确定</u-button>
				</view>
			</u-dropdown-item> -->
		</u-dropdown>
		
		<!-- <u-dropdown ref="uDropdown">
					<u-dropdown-item title="属性">
						<view class="slot-content" style="background-color: #FFFFFF;">
							<scroll-view scroll-y="true" style="height: 200rpx;">
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">无言独上西楼</view>
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">月如钩</view>
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">寂寞梧桐深院锁清秋</view>
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">剪不断</view>
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">理还乱</view>
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">是离愁</view>
								<view class="u-text-center u-content-color u-m-t-20 u-m-b-20">别是一般滋味在心头</view>
							</scroll-view>
							<u-button type="primary" @click="closeDropdown">确定</u-button>
						</view>
					</u-dropdown-item>
				</u-dropdown>
				<u-button type="primary" @click="closeDropdown">确定</u-button> -->
	</view>
</template>

<script>
	export default {
		data(){
			return {
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
			}
		},
		methods:{
			valChange(e){
				console.log('步进器的值',e.value);
			},
			change(index) {
				this.$u.toast(`点击了第${index}项`);
			},
			closeDropdown() {
				this.$refs.uDropdown.close();
			}
		}
	}
</script>

<style>
</style>
