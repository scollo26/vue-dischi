<template>
  <div class="container-60 pt-5 ">
		<div v-if="cards" class="row row-cols-5">
				<Card 
				v-for="(card, index) in cards" :key="index" :image="card.poster" :name="card.title" :title="card.title" :artist="card.author" :year="card.year"/>
			</div>
			<div v-else class="loading">
				<h1>Loading...</h1>
			</div>
			<!-- <div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div>
			<div class="col">
				<div class="spotify">
					<img class="p-3" src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
					<span class="title">new jersy</span>
					<span class="subtitle">Bon Jovi</span>
					<span class="year">1988</span>
				</div>
			</div> -->
	</div>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue';
export default {
  name: "Main",
	components: {
		Card,
	},
	data() {
		return {
			cards: null,
		}
	},
	mounted() {
		setTimeout(() => {
			this.getCards()
		}, 1000);
	},
	methods: {
		getCards() {
			axios.get('https://flynn.boolean.careers/exercises/api/array/music')
			.then((result) => {
				this.cards = result.data.response;
			})
			.catch((error) => {
				console.log(error);
			})
		}
	}
}
</script>

<style lang="scss">
main{
    background-color: #1E2D3B;
}
.container-60 {
	width: 100%;
	// margin: auto;
    background-color: #1E2D3B;
    .row{
        width: 70%;
        margin: 0 auto;
    }
    
	.col {
		padding: 0.5em 1em;
	}
	
}
</style>