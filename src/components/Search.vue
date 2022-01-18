<template>
    <div class="col">
        <label class="font-text p-1" for="">Genere</label>
		<!-- inserimento form -->
		<select v-model="selectedGenere"  @change="$emit('doSearch', selectedGenere)">
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
		</select>
    </div>
</template>

<script>
export default {
    name: "Search",
    data(){
    return{
        selectedGenere : 'all',
        } 
    },

}
</script>

<style lang="scss">
.font-text{
    color: white;
    
}

</style>