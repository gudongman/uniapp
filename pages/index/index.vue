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
		
		<u-divider>input输入框 placeholder-style字符串 custom-style对象</u-divider>
		<u-input focus :selection-start="5" :selection-end="7" v-model="value" border type="text" clearable confirm-type="确定" :placeholder-style="'color:red;fontSize:14px;'" :custom-style="{fontSize: '18px'}"></u-input>
		<u-input type="textarea" border v-model="textareavalue" :height="100" :auto-height="true" :maxlength="-1" ></u-input>
		<u-input v-model="password" border type="password" :password-icon="true" placeholder="请输入密码"></u-input>
		<view class="">
			<u-input v-model="sel" border type="select" @click="inputShow=true" :select-open="inputShow"/>
			<u-action-sheet :list="actionSheetList" v-model="inputShow" @click="change"></u-action-sheet>
		</view>
		
		<u-divider>表单</u-divider>
		<u-form :model="form" ref="uform" :rules="rules" :errorType="['toast']">
			<u-form-item label-width="120" label="姓名" prop="name"><u-input v-model="form.name" type="text"></u-input></u-form-item>
			<u-form-item label-width="120" label="手机号" prop="phone"><u-input v-model="form.phone" type="number"></u-input></u-form-item>
			<u-form-item label="简介"><u-input v-model="form.desc" type="textarea" height="110"></u-input></u-form-item>
			<u-form-item label="性别" prop="sex">
				<u-input v-model="form.sex" type="select" @click="showSex=true" :select-open="showSex"/>
				<u-action-sheet :list="actionSheetList" v-model="showSex" @click="changeGender"></u-action-sheet>
			</u-form-item>
			<u-form-item label="密码" ></u-form-item>
			<u-form-item label="水果"><u-input v-model="form.sex" type="select" /></u-form-item>
		</u-form>
		
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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: 'https://cdn.uviewui.com/uview/example/fade.jpg',
				customStyle: {marginTop: '10upx', width: '100upx'},
				
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
					}]
				}
			}
		},
		onReady() {
			// this.$refs.uform.setRules(this.rules)
				this.$refs.uform.setRules(this.rules);
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
			change(index){
				console.log(index);
				this.sel = this.actionSheetList[index].text
			},
			changeGender(index){
				this.form.sex = this.actionSheetList[index].text
			}
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
