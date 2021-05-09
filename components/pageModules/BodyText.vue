<template>
    <!-- <div class="bodyText-container" v-bind:class="(item.showSitebar)?'one-col':'two-col'"> -->
    <div class="bodyText-container container">
        <SanityContent class="formatting" :blocks="item.body" />
    </div>
</template>

<script>
    import { SanityContent } from '@nuxtjs/sanity/dist/components/sanity-content'
	export default {
		name: "BodyText",
        components: {SanityContent},
        props:{
            item: Object
        }
    }
</script>

<style lang="scss" scoped>

</style>