<template>
    <section class="moooce-how-to-steps">
        <div class="container">
            <div class="row">
                <div class="col-md-7 offset-md-1">
                    <SanityContent class="formatting" v-if="item.text" :blocks="item.text" />
                </div>
            </div>
            <div class="moooce-how-to-container">
                <div class="moooce-how-to-step" v-for="item in item.steps" :key="item._key">
                    <img width="317" height="503" :src="$urlFor(item.image).width(317).height(503)" :alt="item.image.alt" />
                    <div class="how-to-text">
                        <div class="h1" v-text="item.step" />
                        <SanityContent class="formatting" v-if="item.text" :blocks="item.text" />
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import { SanityContent } from '@nuxtjs/sanity/dist/components/sanity-content'
	export default {
		name: "HowToUse",
        components: {SanityContent},
        props:{
            item: Object
        }
    }
</script>

<style lang="scss" scoped>
 

</style>
