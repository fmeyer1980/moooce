<template>
    <nav id="menu-element" class="main-nav bg-primary-shade color-light-glare pt-lg">
        <ul v-for="item in site.asideMenu" :key="item._key">
            <li>
                <nuxt-link :to="{name:'slug',params:{slug:item.slug.current}}" title="Handelsbetingelser">{{ item.name }}</nuxt-link>
            </li>
        </ul>
		<img
            class="main-nav__bg-image"
            src="https://cdn.sanity.io/images/vn5aapzu/production/c10c17f387540ceaf6b4afabd69f2bf5291445d3-1800x1257.jpg?w=1400&q=70&auto=format"
            alt=""
            height="1800"
            width="1200"
            loading="lazy"
        />
    </nav>
</template>

<script>
	import {mapState} from "vuex";
	export default {
		name: "Menu",
		computed: {
            ...mapState('sanity',{
				site: 'siteSettings'
			}),
			...mapState('view', {
				menuOpen: 'menuOpen'
			}),
			routeName(){
				return this.$route.name;
			}
		},
		watch:{
			routeName(to){
				if(this.menuOpen)
					this.$store.commit('view/setMenuOpen',false);
			}
		}
	};
</script>

<style lang="scss" scoped>

.main-nav{
	position: fixed;
	top: -100vh;
	z-index: 50;
	width: 100%;
	min-height: 100vh;
	transition: 300ms ease-in-out;
    transition-property: top;

	.open & {
		top: 0;

	}

	&__bg-image{
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: top center;
		opacity: 0.3;
		z-index: -1;
	}
}

</style>