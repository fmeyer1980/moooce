<template>
	<footer>
		sdsd
		<p v-text="site.name" />
		<p v-text="site.address" />
		<p v-text="site.zip" />
		<p v-text="site.country" />
		<a href="mailto:hey@moooce.com">{{ site.mail }}sdsdd</a>
	</footer>
</template>

<script>
	import {mapState} from 'vuex'
	export default {
		name: "Footer",
		computed:{
			...mapState('sanity',{
				site: 'siteSettings'
			})
		}
	};
</script>

<style lang="scss" scoped>

</style>
