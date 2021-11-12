<script>
export default {
	data() {
		return {
			selectedImage: 0,
			openImage: 0,
			quantity: 1,
			maxQuantity: 50,
			assets: {
				icon: {
					previous: require("@/assets/images/icon-previous.svg"),
					next: require("@/assets/images/icon-next.svg"),
					icon_cart: require("@/assets/images/icon-cart-white.svg"),
				},
				productImage: [
					require("@/assets/images/image-product-1.jpg"),
					require("@/assets/images/image-product-2.jpg"),
					require("@/assets/images/image-product-3.jpg"),
					require("@/assets/images/image-product-4.jpg"),
				],
				thumbnail: [
					require("@/assets/images/image-product-1-thumbnail.jpg"),
					require("@/assets/images/image-product-2-thumbnail.jpg"),
					require("@/assets/images/image-product-3-thumbnail.jpg"),
					require("@/assets/images/image-product-4-thumbnail.jpg"),
				],
			},
		};
	},
	methods: {
		switchImage(state) {
			var ctx = this;

			if (state === 0) {
				let newIndex = ctx.selectedImage - 1;
				if (ctx.assets.productImage[newIndex]) {
					ctx.selectedImage = newIndex;
				}
			} else {
				let newIndex = ctx.selectedImage + 1;
				if (ctx.assets.productImage[newIndex]) {
					ctx.selectedImage = newIndex;
				}
			}
		},
		switchQuantity(state) {
			var ctx = this;

			if (state === 0) {
				let newIndex = ctx.quantity - 1;
				if (newIndex >= 0 && ctx.quantity <= ctx.maxQuantity) {
					ctx.quantity = newIndex;
				}
			} else {
				if (ctx.quantity < ctx.maxQuantity) {
					let newIndex = ctx.quantity + 1;
					ctx.quantity = newIndex;
				}
			}
		},
	},
};
</script>

<template>
	<div>
		<Header></Header>
		<main>
			<section class="product">
				<div class="overlay" v-if="openImage">
					<div class="menu">
						<div class="close" v-on:click="openImage = 0">X</div>
						<div class="image">
							<img
								:src="assets.productImage[selectedImage]"
								alt="Image du produit"
							/>
							<div
								class="left-arrow"
								title="Avant"
								v-on:click="switchImage(0)"
							>
								<div class="box">
									<img
										:src="assets.icon.previous"
										alt="Avant"
									/>
								</div>
							</div>
							<div
								class="right-arrow"
								title="Après"
								v-on:click="switchImage(1)"
							>
								<div class="box">
									<img :src="assets.icon.next" alt="Après" />
								</div>
							</div>
						</div>
						<div class="thumbnail">
							<img
								:src="value"
								v-for="(value, index) in assets.thumbnail"
								:key="index"
								v-on:click="selectedImage = index"
							/>
						</div>
					</div>
				</div>
				<div class="left">
					<div class="image">
						<img
							:src="assets.productImage[selectedImage]"
							alt="Image du produit"
							v-on:click="openImage = 1"
						/>
					</div>
					<div class="thumbnail">
						<img
							:src="value"
							v-for="(value, index) in assets.thumbnail"
							:key="index"
							v-on:click="selectedImage = index"
						/>
					</div>
				</div>
				<div class="details">
					<p class="tag">SNEAKER COMPANY</p>
					<h1>Fall Limited Edition <br />Sneakers</h1>
					<p class="description">
						These low-profile sneakers are your perfect casual
						wear<br />
						companion. Featuring a durable rubber outer sole,
						they’ll<br />
						withstand everything the weather can offer.
					</p>
					<div class="price-menu">
						<div class="price">$125.00</div>
						<div class="percent">50%</div>
					</div>
					<div class="reduction">$250.00</div>
					<div class="buy-menu">
						<div class="quantity-selector">
							<div
								class="less"
								title="Réduire"
								v-on:click="switchQuantity(0)"
							>
								-
							</div>
							<div class="quantity">
								{{ quantity }}
							</div>
							<div
								class="more"
								title="Augmenter"
								v-on:click="switchQuantity(1)"
							>
								+
							</div>
						</div>
						<a class="buy-button" href="javascript:void(1)">
							<img
								:src="assets.icon.icon_cart"
								alt="Icone d'achat"
							/>
							Add to cart
						</a>
					</div>
				</div>
			</section>
		</main>
	</div>
</template>