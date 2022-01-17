<template>
	<div class="col">
    <div class="spotify p-3">
			<img class="pb-3" :src="image" >
			<span class="title pb-1">{{title}}</span>
			<span class="subtitle">{{artist}}</span>
			<span class="year">{{year}}</span>
    </div>
	</div>
</template>

<script>
export default {
	name: "Card",
	props: [
		'image',
		'title',
		'artist',
		'year'
	]
}
</script>

<style lang="scss">
.col {
		padding: 0.5em 1em;
		.spotify {
		background-color: #2D3A46;
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 100%;
		img {
			width: 100%;
		}
		.title {
			text-transform: uppercase;
			color: white;
			font-weight: 500;
		}
		.subtitle{
            color: grey;
        } 
        .year {
			color: grey
		}
	}
	}



</style>