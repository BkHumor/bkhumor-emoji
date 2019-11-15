

    
**简要描述：** 

- 表情插件
版本 v1.0.0
qq表情
基于colorui 通过 vue 实现
表情放在static下的 face目录下。
**注意：手机上运行需要将表情图片放到自己服务器。**

```javascript

模板：
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

JS部分：

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
```

 **备注** 

- 更多详细内容请参看demo！有疑问可留言


欢迎使用ShowDoc！