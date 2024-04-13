<template>
	<div class="phones">
		<h2>My mobiles , oh yeah</h2>
		<input
			v-model="phoneSearch"
			type="text"
			name=""
			id=""
			placeholder="Search on mobile..."
		/>
		<div class="wrapperDiv-phone">
			<div v-for="(phone, idx) in filteredPhones" :key="idx" class="phone">
				<p>{{ phone.brand }}: {{ phone.title }}</p>
				<img :src="phone.thumbnail" alt="" />
				<strong
					><p :style="{ fontSize: '34px' }">${{ phone.price }}</p></strong
				>
				<p>{{ phone.description }}</p>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref, onMounted, computed } from "vue";

const phones = ref([]);
const phoneSearch = ref("");

onMounted(async () => {
	const res = await fetch("https://dummyjson.com/products");
	const mobiles = await res.json();

	phones.value = mobiles.products;
	console.log(mobiles.products);
});

const filteredPhones = computed(() => {
	const regex = new RegExp(phoneSearch.value, "gi");
	if (!phoneSearch.value) {
		return phones.value;
	} else {
		return phones.value.filter((phone) => {
			return (
               phone.brand.match(regex) ||
               phone.title.match(regex) ||
               phone.price === parseFloat(phoneSearch.value) ||
               phone.description.match(regex)
			);
		});
	}
});
</script>

<style scoped>
	.phones {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.phones input {
		width: 200px;
		margin: auto;
		padding: 0.7rem;
		border-radius: 10px;
		outline: none;
		border: none;
		box-shadow: 1px 2px 15px rgba(0, 0, 0, 0.4);
	}
	.phones h2 {
		font-size: 60px;
		margin: 15px 0;
	}
	.wrapperDiv-phone {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: center;
		gap: 15px;
	}

	.phone {
		padding: 1.2rem;
		border: 3px solid #e3e3e3;
		width: calc(33% - 30px);
		border-radius: 0 22px 0 22px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.phone > img {
		width: 380px;
		height: 300px;
		object-position: center;
	}

	@media (max-width: 1200px) {
		.wrapperDiv-phone {
			flex-direction: column;
			padding-top: 60px;
		}

		.wrapperDiv-phone .phone {
			width: 100%;
		}
	}
</style>
