<template>
	<view class="">
		<u-divider>uview </u-divider>
		<u-row gutter="16">
			<u-col span='4'>
				<u-button @click="navTo('/pages/index/index')">组件1</u-button>
			</u-col>
			<u-col span='4' ><u-button @click="navTo('/pages/index/index2')">组件2</u-button></u-col>
			<u-col span='4'><u-button>uview JS</u-button></u-col>
		</u-row>
		
		<u-divider>抽奖页面</u-divider>
		<u-row gutter="16">
			<u-col span='4'>
				<u-button @click="navTo('/pages/index/draw')">抽奖页面</u-button>
			</u-col>
			<u-col span='4'><u-button   @click="navTo('/pages/index/drawThink')">抽奖页面的思路</u-button></u-col>
		</u-row>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				
			}
		},
		methods:{
			navTo(url){
				console.log(url);
				this.$u.route(url)
			}
		}
	}
</script>

<style>
</style>
