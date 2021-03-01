<template>
	<view class="wrap">
		<u-button shape="circle" type="primary" ripple></u-button>
		
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
		
		<u-divider>input输入框 placeholder-style字符串 custom-style对象</u-divider>
		<u-input focus :selection-start="5" :selection-end="7" v-model="value" border type="text" clearable confirm-type="确定" :placeholder-style="'color:red;fontSize:14px;'" :custom-style="{fontSize: '18px'}"></u-input>
		<u-input type="textarea" border v-model="textareavalue" :height="100" :auto-height="true" :maxlength="-1" ></u-input>
		<u-input v-model="password" border type="password" :password-icon="true" placeholder="请输入密码"></u-input>
		<view class="">
			<u-input v-model="sel" border type="select" @click="inputShow=true" :select-open="inputShow"/>
			<u-action-sheet :list="actionSheetList" v-model="inputShow" @click="change"></u-action-sheet>
		</view>
		
		<u-divider>表单 error-type为['toast'] 仅在有提交按钮的时候会展示</u-divider>
		<u-form :model="form" ref="uform" :rules="rules" :error-type="['message']">
			<!-- :error-type="['message','border-bottom']" -->
			<u-form-item left-icon="account" label-width="120" label="姓名" prop="name"><u-input v-model="form.name" type="text"></u-input></u-form-item>
			<u-form-item label-width="120" label="手机号" prop="phone"><u-input v-model="form.phone" type="number"></u-input></u-form-item>
			<u-form-item label="简介" prop="desc"><u-input v-model="form.desc" type="textarea" height="110"></u-input></u-form-item>
			<u-form-item label="性别" prop="sex">
				<u-input v-model="form.sex" type="select" @click="showSex=true" :select-open="showSex"/>
				<u-action-sheet :list="actionSheetList" v-model="showSex" @click="changeGender"></u-action-sheet>
			</u-form-item>
			<u-form-item  label-width="160" label="密码" prop="pwd"><u-input type="password" v-model="form.pwd" password-icon></u-input></u-form-item>
			<u-form-item  label-width="160" label="确认密码" prop="repwd"><u-input type="password" v-model="form.repwd" password-icon></u-input></u-form-item>
			<u-form-item label="水果" prop="fruit"><u-checkbox-group @change="fruitChange" max="2"><u-checkbox shape="circle" v-model="item.checked" v-for="(item,index) in checkboxList" :key="index" :name="item.name">{{item.name}}</u-checkbox></u-checkbox-group></u-form-item>
			<u-form-item label="单选" prop="fruitRadio"><u-radio-group @change="radioChange" v-model="radioValue"><u-radio shape="circle" :name="item.name" v-for="(item,index) in radioList" :key="index" >{{item.name}}</u-radio></u-radio-group></u-form-item>
			<u-form-item label="开关" prop="switch"><u-switch slot="right" v-model="form.switch"></u-switch></u-form-item>
			<u-button @click="submit">提交</u-button>
		</u-form>
		<u-divider>日历</u-divider>
		<u-calendar v-model="calendarShow" mode="date" @change="changeCalendar"></u-calendar>
		<u-input type="select" :select-open="calendarShow" v-model="date" @click="calendarShow= true"></u-input>
		<u-divider>日历区域选择</u-divider>
		<u-calendar v-model="calendarRangeShow" mode="range" @change="changeCalendarRange" start-text="到店" end-text="离店">
			<view slot="tooltip">
				<view style="text-align: center;line-height: 50px;font-size: 16px;">
					选择住店日期
				</view>
			</view>
		</u-calendar>
		<u-input type="select" :select-open="calendarRangeShow" v-model="dateRange" @click="calendarRangeShow= true"></u-input>
		
		<u-divider>Select 列选择器</u-divider>
		<!-- <u-select v-model="selShow" :list="list" @confirm="confirm"></u-select>
		<u-button @click="selShow=true">{{choosen||'请选择'}}</u-button> -->
		
		<u-select v-model="selShow" :list="mulList" @confirm="confirm" mode="mutil-column"></u-select>
		<u-button @click="selShow=true">{{choosen||'请选择'}}</u-button> 
		
		<!-- <u-keyboard ref="uKeyboard" mode="car" v-model="show"></u-keyboard>
		<u-button @click="show = true">打开</u-button> -->
		
		<u-divider>picker 选择器</u-divider>
		
		<u-divider>表格</u-divider>
		<u-table >
			<u-tr>
				<u-th>学校</u-th>
				<u-th>班级</u-th>
				<u-th>年龄</u-th>
			</u-tr>
			<u-tr>
				<u-td width="auto">浙江大学</u-td>
				<u-td width="16%">二年级</u-td>
				<u-td width="17%">的说辞</u-td>
				<u-td width="auto">22</u-td>
			</u-tr>
			<u-tr>
				<u-td>清华大学</u-td>
				<u-td >
					<view class="">
						<text>二年级</text> <text style="color:blue;padding-left: 5px;">的</text>
					</view>
				</u-td>
				<u-td>20</u-td>
			</u-tr>
		</u-table>
		
		
		<!-- 11111111111111111111111 2-4 晚上写的哦 -->
		<!-- picker 选择器  -->
		<!-- <u-divider> picker 选择器 </u-divider>
		<u-picker v-model="pickerShow"></u-picker> -->
		
		<u-count-to :start-val="startVal" :end-val="endVal" use-easing :duration="3000" ref="count" :decimal="2"></u-count-to>
		<u-button @click="add">+100</u-button>
		
		
		<u-card :show-head="false" :show-foot="false">
			<!-- :title="title" :sub-title="subTitle" :thumb="thumb" -->
			<view class="" slot="body">
				<view class="u-body-item u-flex u-border-bottom u-col-between u-p-t-0">
					<view class="u-body-item-title u-line-2">瓶身描绘的牡丹一如你初妆，冉冉檀香透过窗心事我了然，宣纸上走笔至此搁一半</view>
					<image src="https://img11.360buyimg.com/n7/jfs/t1/94448/29/2734/524808/5dd4cc16E990dfb6b/59c256f85a8c3757.jpg" mode="aspectFill"></image>
				</view>
				<view class="u-body-item u-flex u-row-between u-p-b-0">
					<view class="u-body-item-title u-line-2">釉色渲染仕女图韵味被私藏，而你嫣然的一笑如含苞待放</view>
					<image src="https://img12.360buyimg.com/n7/jfs/t1/102191/19/9072/330688/5e0af7cfE17698872/c91c00d713bf729a.jpg" mode="aspectFill"></image>
				</view>
			</view>
			<view class="" slot="foot"><u-icon name="chat-fill" size="34" color="" label="30评论"></u-icon></view>
		</u-card>
		
		<u-divider> mask 遮罩层 </u-divider>
		<u-divider> @tap.stop防止点击弹窗关闭遮罩层 </u-divider>
		<u-divider> zoom true 弹出框变大 </u-divider>
		<u-mask :show="maskshow" @click="maskshow = false" :zoom="true">
			<view class="warp">
				<view class="rect" @tap.stop="clickMask">点击</view>
			</view>
		</u-mask>
		<u-button @click="maskshow = true">mask弹出</u-button>
		<u-divider> 轮播 </u-divider>
		<u-divider>mode round/dot/number/rect/none </u-divider>
		<u-swiper :list="swiperlist" mode="round" title :effect3d="effect3d"></u-swiper>
		
		<u-button  @click="effect3d=!effect3d" style="margin-top: 2px;">开启/关闭3d效果</u-button>
		
		<u-link href="http://www.uviewui.com">蜀道难，难于上青天</u-link>
		
		
		<!-- <u-tabs-swiper ref="tabs" :list="list" bar-height="6" bar-width="40" active-color="#2979ff"></u-tabs-swiper> -->
		<u-tabs-swiper ref="tabs"  :list="namelist"  bar-height="6" bar-width="40" active-color="#2979ff"></u-tabs-swiper>
		<!-- <u-tabs-swiper ref="tabs" :list="list" name="cate_name" count="cate_count" active-color="#2979ff" inactive-color="#606266" font-size="30" current="0"></u-tabs-swiper> -->
		<newCom></newCom>
		
		<u-button shape="circle" type="primary" ripple @click="go()">新的页面</u-button>
	</view>
</template>

<script>
	import newCom from './components/new-component.vue'
	export default {
		components: {newCom},
		data() {
			return {
				
				list: [{
					cate_name: '待收货'
				}, {
					cate_name: '待付款'
				}, {
					cate_name: '待评价',
					cate_count: 5
				}],
				namelist: [{
					name: '待收货'
				}, {
					name: '待付款'
				}, {
					name: '待评价',
					count: 5
				}],
				src: 'https://cdn.uviewui.com/uview/example/fade.jpg',
				customStyle: {marginTop: '10upx', width: '100upx'},
				calendarShow: false,
				calendarRangeShow: false,
				show: true,
				inputShow: false,
				showSex:false,
				value:'实打实的撒耳温枪',
				textareavalue: '',
				password:'',
				sel:'',
				actionSheetList: [
					{
						text: '男'
					},
					{
						text: '女'
					},
					{
						text: '保密'
					}
				],
				checkboxList: [
					{
						name: '苹果',
						checked: false,
						disabled: false
					},
					{
						name: '雪梨',
						checked: false,
						disabled: false
					},
					{
						name: '柠檬',
						checked: false,
						disabled: false
					}
				],
				radioList:[{
					name: '苹果',
					disabled: false
				},{
					name: '香蕉',
					disabled: false
				}],
				radioValue: '苹果',
				form:{
					name:''
				},
				rules:{
					name:[{
						required: true,
						message: '请输入姓名',
						// trigger: ['blur','change'],
						trigger: 'blur,change'
					}],
					phone:[{
						required: true,
						message: '请输入手机号',
						trigger:'blur,change'
					},{
						validator: (rule, value,callback)=>{
							return this.$u.test.mobile(value)
						},
						message: '手机号输入不正确',
						trigger:'blur,change'
					}],
					pwd:[{
						required: true,
						message: '请输入密码',
						trigger:'blur,change'
					}],
					repwd:[{
						required: true,
						message: '请确认密码',
						trigger:'blur,change'
					},{
						validator: (rules, valid,callback)=>{
							return this.form.pwd==this.form.repwd
						},
						message: '两次密码输入不一致',
						trigger:'blur'
					}]
				},
				// 2-4 晚上写的哦 
				maskshow: false,
				endVal: 300.33,startVal:20,
				thumb: 'http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg',
				swiperlist: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
				effect3d: false,
				date:'选择日期',
				dateRange:'选择日期区间',
				selShow: false,
				list: [
					{
						value: '1',
						label: '江'
					},
					{
						value: '2',
						label: '湖'
					}
				],
				mulList: [[
					{
						value: '1',
						label: '江'
					},
					{
						value: '2',
						label: '湖'
					}
				],[
					{
						value: '3',
						label: '江2'
					},
					{
						value: '4',
						label: '湖2'
					}
				]],
				choosen: ''
			}
		},
		onReady() {
			// this.$refs.uform.setRules(this.rules)
				this.$refs.uform.setRules(this.rules);
		},
		onLoad() {

		},
		methods: {

			fruitChange(e){
				this.form.fruit = e;
			},
			radioChange(e){
				this.form.fruitRadio = e;
			},
			
			go(){
				uni.navigateTo({
					url: '/pages/index/index2'
				})
			},// 2-4 晚上写的哦 
			clickMask(){
				console.log(11111);
			},
			add(){
				this.startVal = Number(this.$refs.count.displayValue);
				console.log(this.startVal);
				this.endVal+=100;
			},
			// 
			confirm(e){
				console.log(e)
				// this.choosen=e[0];
				 this.choosen=e[0].label+'-'+e[1].label ;
			},
			changeCalendarRange(e){
				console.log(e);
				this.dateRange = e.startDate +'至' +e.endDate
			},
			changeCalendar(e){
				console.log(e);
				this.date = e.result
			},
			alert(index){
				console.log(index);
			},
			close(){
				this.show = false
			},
			change(index){
				console.log(index);
				this.sel = this.actionSheetList[index].text
			},
			changeGender(index){
				this.form.sex = this.actionSheetList[index].text
			},
			submit(){
				this.$refs.uform.validate(valid=>{
					console.log(valid);
					console.log(this.form);
					if(valid){
						this.$u.toast('验证通过')
					}else{
						this.$u.toast('验证失败')
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
// 2-4 晚上写的哦 
	.u-card-wrap { 
			background-color: $u-bg-color;
			padding: 1px;
		}
		
		.u-body-item {
			font-size: 32rpx;
			color: #333;
			padding: 20rpx 10rpx;
		}
			
		.u-body-item image {
			width: 120rpx;
			flex: 0 0 120rpx;
			height: 120rpx;
			border-radius: 8rpx;
			margin-left: 12rpx;
		}
	.warp {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100%;
	}
	.rect {
		width: 120px;
		height: 120px;
		background-color: #fff;
	}
	//
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
