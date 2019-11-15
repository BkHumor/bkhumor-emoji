<template>
	<view class="">
		
		<view class="text-area">
			<text class="title text-center">表情插件示例</text>
		</view>
		<view class="bg-white emj_box">
			
		
		<view class="flex">
			<view class="flex-sub padding-left-xs" style="align-self: center;">
				<input type="text" @focus="InputFocus" @blur="InputBlur" :value="inputValue" placeholder-style="font-size:24rpx;color:#aaaaaa;"  placeholder="请输入您要发送的内容" maxlength="300"></input>
			</view>
			
			<view class="text-center" style="width: 80rpx; font-size: 50rpx;">
				<text :class="emojiIcon" @tap="showEmj"></text>
			</view>
			<button class="cu-btn bg-gradual-blue shadow-blur">发送</button>
		</view>
		<emotion @emotion="handleEmj" :height="200" v-if="isShowEmj"></emotion>
		</view>
	</view>
</template>

<script>
	import emotion from '@/components/bkhumor-emoji/index.vue';
	
	export default {
		data() {
			return {
				title: 'Hello',
				isShowEmj: false,
				emojiIcon:'cuIcon-emoji',
				inputValue:''
			}
		},
		onLoad() {

		},
		components:{
			emotion
		},
		methods: {
			handleEmj(i) {
				
				if(i == '[em_98]') {
					//匹配最后一个表情符号并删除。
					this.inputValue = this.inputValue.replace(/(\[[^\]]+\]|[\s\S])$/, '');
				} else {
					this.inputValue += i;
				}
			},
			showEmj() {
				let bool = !this.isShowEmj;
				if(bool) {
					this.emojiIcon = 'cuIcon-keyboard';
				} else {
					this.emojiIcon = 'cuIcon-emoji';
				}
				
				this.isShowEmj = bool;
				this.$emit('show')
			},
			InputBlur(e){
				
			},
			InputFocus(e){
				this.isShowEmj = false;
				this.$emit('foc')
			},
		}
	}
</script>

<style>


	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.emj_box {
		padding: 15rpx 0 15rpx 0;
		position:fixed; width:100%;
		margin:0 auto; left:0;
		right:0;  bottom:0; 
		border-top: 1px solid #EEEEEE;
	}
</style>
