<template>
	<div class="phones">
		<h2>My mobiles , oh yeah</h2>
		<div class="wrapperDiv-phone">
			<div v-for="(phone, idx) in phones" :key="idx" class="phone">
				<p>{{ phone.brand }}: {{ phone.title }}</p>
                <img :src="phone.thumbnail" alt="">
                <strong><p :style="{fontSize:'34px'}" >${{phone.price}}</p></strong>
				<p>{{ phone.description }}</p>
			</div>
		</div>
	</div>
</template>


<script setup>
	import { ref, onMounted } from "vue";

	const phones = ref([]);

	onMounted(async () => {
		const res = await fetch("https://dummyjson.com/products");
		const mobiles = await res.json();

		phones.value = mobiles.products;
		console.log(mobiles.products);
	});
</script>



<style scoped>
	.phones {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
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
    .phone>img {
        width: 380px;
        height: 300px;
        object-position: center;
    }
</style>