<template>
	<view class="app">
		<!-- 3d轮播图 -->
		<view class="top">
			<local-swiper></local-swiper>
		</view>
		<view>
			<waterfall-flow :list="list" :loading="loading" @click="choose"></waterfall-flow>
		</view>
	</view>
</template>
<script>
	import WaterfallFlow from '@/components/nairenk-waterfall-flow/nairenk-waterfall-flow.vue';
	import localSwiper from "./component/local-swiper.vue"; //3d轮播图组件
	var bitmap1 = null;
	var data = require('@/common/data/data.json');
	var iconTag = 1;
	export default{
		data(){
			return{
				page:1,
				start:0,
				end:0,
				loading:true,
				list:[]
			}
		},
		mounted() {
			this.getList();
		},
		onReachBottom() {
			this.page++;
			this.loading=true;
			this.getList();
		},
		onShow() {
			var icon = plus.nativeObj.View.getViewById("icon");
			if(icon&&iconTag==2){
				setTimeout(function(){
						icon.show();
				},100)
			}
		},
		
		onLoad() {
			this.loadExection()
			if(iconTag==2){
				bitmap1 = new plus.nativeObj.Bitmap('bmp');
				bitmap1.load('/static/navBar/logo.png',function(){
				},function(e){
				
				});
				this.createtab();
			}
		},
		methods:{
			loadExection:function(){
				uni.navigateTo({
					url:"../guide/guide"
				});
				iconTag=2;
			},
			createtab:function(){
				var leftPos = Math.ceil((plus.screen.resolutionWidth - 60) / 2);
				var view = new plus.nativeObj.View('icon', {
					bottom: '11px',
					left:  leftPos+'px',
					width: '60px',
					height: '60px'
				});
				view.drawBitmap(bitmap1,
					{
						tag: 'font',
						id: 'icon',
						//text: '\ue510', //此为字体图标Unicode码'\e600'转换为'\ue600'
						src: '/static/navBar/logo.png',
						position: {
							top: '0px',
							left: '5px',
							width: '50px',
							height: '100%'
						}
					}
				);
				view.addEventListener("click", function(e) {
					uni.switchTab({
						url: '../services/goods'
					})
				}, false);
				view.show();
			},
			choose(item){
					console.log(item)
			},
			getList(){
					if(this.list.length<data.list.length){
						setTimeout(()=>{
							this.end = this.page * 10;
							this.list = this.list.concat(data.list.slice(this.start,this.end));
							this.start = this.end;
							setTimeout(()=>{
								this.loading=false;
							},120);
						},1000)
					} else{
						this.loading=false;
					}
			}
		},
		components:{
				WaterfallFlow,
				localSwiper
		}
	}
</script>

<style>
	.app{
		height: 100%;
	}
	.top{
		width: 100%;
	}
</style>

