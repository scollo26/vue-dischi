<template>

  <div class="container-60 pt-5 ">
	  <div class="container ">
            <div class="row select ">
                <!-- <div class="col">
					
					<select v-model="selected" @change="Value"  >
						<option value="all">All</option>
						<option value="rock">Rock</option>
						<option value="pop">Pop</option>
						<option value="jazz">Jazz</option>
						<option value="metal">Metal</option>
					</select>
                </div> -->

				<!-- collegamento figlio Search per la ricerca di genere -->
                <Search @doSearch="Value($event)"/>
				
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
import Search from './Search.vue';
export default {
  name: "Main",
	components: {
		Card,
		Search,
	},
	data() {
		return {
			cards: null,
			// selected: 'all',
			arrayOrigi: null,
			selectArti: 'all',
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
				// array originale
				this.arrayOrigi = result.data.response;
			})
			.catch((error) => {
				console.log(error);
			})
		},
		// funzione per form selected
		Value: function (text){
			this.cards = this.arrayOrigi
			if (text != 'all') {
				this.cards = this.cards.filter(element => 
				element.genre.toLowerCase()  === text);
			} else {
				return this.cards;
			}
			return this.cards;
			
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