<template>
<div>
    <div v-for="item in pages.pageModules" :key="item._id">
        <component :is="componentMap[item._type]" :item="item" />
    </div>
</div>
</template>

<script>
import { groq } from '@nuxtjs/sanity'

import BodyText from '@/components/pageModules/BodyText'
import ImageTextbox from '@/components/pageModules/ImageTextbox'
import HowToUse from '@/components/pageModules/HowToUse'
import Intro from '@/components/pageModules/Intro'
import PriceList from '@/components/pageModules/PriceList'
import CoverImage from '@/components/pageModules/CoverImage'


export default {
    async asyncData({ params, $sanity }) {
        const query = groq`*[_type == "pages" && slug.current == "${params.slug}"]{
            name,
            slug,
            headline,
            summary,
            showSitebar,
            hidePageHeader,
            pageModules[]{
                _key,
                products[]->,
                ...,
            }
        }[0]`
        const pages = await $sanity.fetch(query)
        return { pages }
    },
    data(){
        return {
            componentMap: {
                bodyText: BodyText,
                imageTextBox: ImageTextbox,
                howToUse: HowToUse,
                intro: Intro,
                priceList: PriceList,
                coverImage: CoverImage
            }
        }
    }
}
</script>
