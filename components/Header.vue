<script>
export default {
	data() {
		return {
			openMenu: 0,
			productsInCart: [
				{
					name: "Fall Limited Edition Sneakers",
					image: require("@/assets/images/image-product-1-thumbnail.jpg"),
					price: 125,
					quantity: 3,
				},
				{
					name: "Fall Limited Edition Sneakers",
					image: require("@/assets/images/image-product-1-thumbnail.jpg"),
					price: 125,
					quantity: 3,
				},
				{
					name: "Fall Limited Edition Sneakers",
					image: require("@/assets/images/image-product-1-thumbnail.jpg"),
					price: 125,
					quantity: 3,
				},
			],
			assets: {
				icone_delete: require("@/assets/images/icon-delete.svg"),
				image_avatar: require("@/assets/images/image-avatar.png"),
				icon_cart: require("@/assets/images/icon-cart.svg"),
				icon_close: require("@/assets/images/icon-close.svg"),
			},
		};
	},
};
</script>

<template>
	<header class="header">
		<nav>
			<ul class="menu-nav">
				<li
					class="menu-icon"
					title="Menu"
					tabindex="0"
					v-on:click="openMenu = 1"
				>
					<img
						:src="require('@/assets/images/icon-menu.svg')"
						alt="Menu"
						class="menu-icon"
					/>
				</li>
				<li class="name">
					<a href="javascript:void(1);"
						><img
							:src="require('@/assets/images/logo.svg')"
							alt="Logo"
					/></a>
				</li>
				<li class="item">
					<a href="javascript:void(1);">Collections</a>
				</li>
				<li class="item"><a href="javascript:void(1);">Men</a></li>
				<li class="item"><a href="javascript:void(1);">Women</a></li>
				<li class="item"><a href="javascript:void(1);">About</a></li>
				<li class="item"><a href="javascript:void(1);">Contact</a></li>
			</ul>
			<aside class="overlay" v-if="openMenu">
				<div class="menu">
					<div
						class="close"
						title="Fermer le menu"
						v-on:click="openMenu = 0"
					>
						<img :src="assets.icon_close" alt="Fermer le menu" />
					</div>
					<div class="list">
						<ul class="menu-list">
							<li>
								<a href="javascript:void(1);">Collections</a>
							</li>
							<li>
								<a href="javascript:void(1);">Men</a>
							</li>
							<li>
								<a href="javascript:void(1);">Women</a>
							</li>
							<li>
								<a href="javascript:void(1);">About</a>
							</li>
							<li>
								<a href="javascript:void(1);">Contact</a>
							</li>
						</ul>
					</div>
				</div>
			</aside>
		</nav>

		<div class="right">
			<div class="basket" title="Panier d'achat" tabindex="0">
				<img
					class="basket-img"
					:src="assets.icon_cart"
					alt="Panier d'achat"
				/>
				<div class="basket-tab">
					<div class="title">Cart</div>
					<div class="empty-cart" v-if="productsInCart.length === 0">
						Your card is empty.
					</div>
					<div class="body-cart" v-if="productsInCart.length >= 1">
						<div
							class="card"
							v-for="(value, index) in productsInCart"
							:key="index"
						>
							<div class="image">
								<img :src="value.image" :alt="value.name" />
							</div>
							<div class="details">
								<p>{{ value.name }}</p>
								<p>
									${{ value.price }} x {{ value.quantity }}
									<span class="price"
										>${{
											value.price * value.quantity
										}}</span
									>
								</p>
							</div>
							<div class="trash">
								<img
									:src="assets.icone_delete"
									alt="Supprimer ce produit"
									title="Supprimer ce produit"
								/>
							</div>
						</div>
						<div class="btn">
							<a class="btn-style" href="javascript:void(1)"
								>Checkout</a
							>
						</div>
					</div>
				</div>
			</div>
			<div class="profil" title="Photo de profil" tabindex="0">
				<img :src="assets.image_avatar" alt="Photo de profil" />
			</div>
		</div>
	</header>
</template>