<template>

<section class="moooce-help-support">
    <img :src="$urlFor(item.bgImage).width(1800)" :alt="item.bgImage.alt" loading="lazy" />
    <div class="container">
        <div class="row">
            <div class="col-md-10 offset-md-1">
                <h1 v-text="item.headline" />
                <p v-text="item.subHeadline" />
            </div>
            <div class="col-lg-5 offset-lg-2 col-md-7 offset-md-1">
                
                <div class="moooce-info-box">
                    <SanityContent class="text" :blocks="item.body" />
                    <div class="moooce-community" v-if="item.facebookUrl || item.linkUrl">
                        <a :v-if="item.facebookUrl" :href="item.facebookUrl" target="_blank" title="Moooce community  på Facebook">
                            <svg aria-hidden="true" class="svg-inline--fa fa-facebook-square fa-w-14" data-icon="facebook-square" data-prefix="fab" viewBox="0 0 448 512" xmlns="http://www.w3.org/2000/svg"><defs/><path d="M400 32H48A48 48 0 000 80v352a48 48 0 0048 48h137.25V327.69h-63V256h63v-54.64c0-62.15 37-96.48 93.67-96.48 27.14 0 55.52 4.84 55.52 4.84v61h-31.27c-30.81 0-40.42 19.12-40.42 38.73V256h68.78l-11 71.69h-57.78V480H400a48 48 0 0048-48V80a48 48 0 00-48-48z" fill="currentColor"/></svg>
                        </a>
                        <div :v-if="item.linkUrl" class="moooce-btn moooce-community-btn">
                            <a :href="item.linkUrl" target="_blank" title="Moooce community på Facebook">{{ item.linkText }}</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
</template>

<script>
    import { SanityContent } from '@nuxtjs/sanity/dist/components/sanity-content'
	export default {
		name: "Intro",
        components: {SanityContent},
        props:{
            item: Object
        }
    }
</script>

<style lang="scss" scoped>
	

</style>