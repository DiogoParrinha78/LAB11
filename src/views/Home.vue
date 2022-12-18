<template >
	<div id="app" style="background-color: grey;">
		<Header />
		<div class="Menu">
			<tr v-for="product in products" :key="product.id">
				<div class="card">
					<img class="img" :src="require(`@/assets/images/${product.image}`)">
					<div class="container text-center">
						<h4><b>{{ product.name }}</b></h4>
						<p>{{ product.description }}.</p>
						<p>Preço {{ product.price }}€</p>
						<form @submit.prevent="add(product.id)">
							<button class="btn btn-dark " type="submit" style="color: #00FF00; ">Buy</button>
						</form>
					</div>
				</div>
			</tr>
		</div>
		<Footer />
	</div>
</template>
  
<script>
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'

export default {
	showModal: true,
	components: {
		Footer,
		Header
	},
	data() {
		return {
			products: [],
		}
	},
	mounted() {

	},

	async add(id) {
		if (this.userLoggedin) (console.log(this.$store.getters['use/getuser']));
		console.log(id);
		const addProduct = this.$store.commit('basket/incrementProduct', id);
		if (addProduct) {
			console.log(id);
			this.$router.push({ path: '/message/5' })
		}
		else {
			this.$router.push({ path: '/message/6' })
		}


	},
	methods: {


	},
	computed: {

	},
	created: async function () {
		const getProduct = await this.$store.dispatch('products/getProductsFromDB');
		if (getProduct) {
			this.products = this.$store.getters['products/getProducts'];
			console.log(this.products);
		}
	}
}
</script>
  
<style scoped>
.Menu {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	grid-template-rows: 1fr 1fr 1fr;
	margin-bottom: 50px;
}

.card {
	margin: 20px;
}
</style>