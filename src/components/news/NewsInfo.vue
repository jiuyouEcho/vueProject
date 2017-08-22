<template>
	<div class="templateDiv">
		<div class="title">
			<h3>{{info.title}}</h3>
			<p>{{info.add_time | dateFmt("YYYY-MM-dd HH:mm:ss")}} {{info.click}}次浏览</p>
		</div>
		<div class="content"v-html="info.content"></div>

	</div>
</template>

<script>
	export default {
		data:function(){
			return {
				info:{}
			};
		},

		created:function(){
			var newsId = this.$route.params.id;
			// console.log(newsId);
			// var url = "http://139.199.192.48:8888/api/getnew/" + newsId;
			var url = this.$urlPrefix + "/api/getnew/" + newsId;
			this.$http.get(url).then(function(response){
				this.info=response.body.message[0];
			});

		}
	}
</script>

<style scoped>
	.title{
		color:#0094ff;
	}

</style>
