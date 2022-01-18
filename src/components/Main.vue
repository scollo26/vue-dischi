<template>

  <div class="container-60 pt-5 ">
	  <div class="container ">
            <div class="row select ">
                <div class="col">
					<!-- <select class=" form-select form-select-sm " aria-label=".form-select-sm example">
                    <option selected>Seleziona Genere</option>
						<option value="Rock">Rock</option>
						<option value="Pop">Pop</option>
						<option value="Jazz">Jazz</option>
						<option value="Metal">Metal</option>
                	</select> -->
					<select v-model="selected"  >
						<option value="all">All</option>
						<option value="rock">Rock</option>
						<option value="pop">Pop</option>
						<option value="jazz">Jazz</option>
						<option value="metal">Metal</option>
					</select>
                </div>
                
            </div>
        </div>
		<div v-if="cards" class="row row-cols-5">
				<Card 
				v-for="(card, index) in cards" :key="index" 
                :image="card.poster" 
                :title="card.title" 
                :artist="card.author" 
                :year="card.year"
				:genre="card.genre"/>
		</div>
		<div v-else class="loading text-center">
			<h1>Loading...</h1>
		</div>
                
	</div>
</template>

<script>
// importazione axiox e figlio card
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
			selected: 'all',
			arrayOrigi: null,
			Api: "https://flynn.boolean.careers/exercises/api/array/music"
			
			
		}
	},
	mounted() {
		setTimeout(() => {
            // richiamo funzione dopo il set timeout
			this.getCards()
		}, 1000);
	},
    // funzione
	methods: {
		getCards() {
            // richiamo server
			axios.get(this.Api)
			.then((result) => {
				console.log(result);
				this.cards = result.data.response;
				this.arrayOrigi = result.data.response;
			})
			.catch((error) => {
				console.log(error);
			})
		},
		
		

	}
}
</script>

<style lang="scss" >
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
    .loading{
        color: honeydew;
    }
    .container{
		.select{ 
			width: 20%;
			margin: 0 auto;
			.form-select{
				text-align: center;
    
			}
		}
	}
	
	
}
</style>