<template>
	<view>
		<common-header :city="city"></common-header>
		</view>
</template>

<script>
	import commonHeader from "../../components/common-header/common-header.vue";
	export default{
		components:{
			commonHeader
		},
		data(){
			return{
				text:"社区",
				city:"上海"
			}
		}
	}
</script>

<style>
</style>
