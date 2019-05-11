<template>
	<view calss="app">
		<waterfall-flow :list="list" :loading="loading" @click="choose"></waterfall-flow>	
	</view>
</template>

<script>
	import WaterfallFlow from '@/components/nairenk-waterfall-flow/nairenk-waterfall-flow.vue';
	var data = require('@/common/data/data.json');
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
		methods:{
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
		components: {
			WaterfallFlow
		}
	}
</script>

<style>
	.app{
		height: 100%;
	}
</style>
